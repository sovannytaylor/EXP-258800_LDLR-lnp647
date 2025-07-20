# EXP-258800_LDLR-lnp647

*Advice for use*: This repository uses core scripts managed in a separate repository ([punctalyze](https://github.com/ocarmo/punctalyze)) to promote modularity and code reuse across projects. e module which is under heavy construction. The checklist below outlines the steps to initiate an experiment repository in a tidy manner and add the analysis submodule. The punctalyze module is under heavy construction, any changes should be committed in a non-breaking manner, as they link to the main branch. Where experiment specific changes are required, consider creating a new csat_calcs branch. Please check off the tick boxes with an 'x' as you go. This repository assumes elementary knowledge of python and git.

### if you have not already forked the punctalyze repository:
- [x] fork the core pipeline if you have not already
        visit the [punctalyze](https://github.com/ocarmo/punctalyze) and click **"Fork"**
        this gives you a personal copy at `https://github.com/YOUR_USERNAME/punctalyze`
- [x] clone your fork locally by clicking **"<>Code"** at the top right of the GitHub page, then **"Open with GitHub Desktop"**
- [x] select your local path and open the repo by clicking the **"open in VS Code"** option
- [x] create a new branch named yourname_dev, always use this branch when making changes
- [x] continue to the checklist below

### if you already forked punctalyze: make your own image analysis repo
- [x] click the **"Use this template"** button at the top right of this template repository
- [x] name your project and click **"Create repository from template"**
- [x] clone onto your local device
- [x] uncomment raw_data folders in gitignore 
- [x] delete placeholder files raw_data folders
- [x] import the editable analysis submodule in vscode terminal: 
~~~ 
git submodule add https://github.com/your_github/your_punctalyze_branch.git punctalyze 
git submodule update --init --recursive
~~~
        ^^^ this adds the shared punctalyze pipeline to your repository
- [x] update *header* at top of README.md and *experiment details* below
- [x] upload raw data, or update the input_path in ```1_initial_cleanup.py```

## Experiment details

**Purpose**: 
Detecting and analyzing intensity and puncta of K562 cells after treatment with LNP-647 carrying mRNA-GFP. This experiment takes not only cells from 90 minutes, but also after 24 hours of treatment. 

**Cell Type**: 
K562 cells

**Instrument/techniques**: 
LSM900, 1024x1024, EGFP, Alexa-fluor 647, 4x averaging, 0.5 scan zoom, taken with definite focus settings, NEED TO INPUT THE REST OF THE SETTINGS LATER 

**Data produced:** 
See results folder

**Analysis:** 
- scrape data from online if necessary
- initial wrangling of images into numpy arrays
- cell segmentation
- segmentation validation
- detecting puncta (foci of high-intensity pixels) and extracting feature information per punctum
- averaging puncta feature information per cell
- plotting

## Making contributions to punctalyze
### if you make changes to your fork that you want to merge to the main branch at [punctalyze](https://github.com/ocarmo/punctalyze):
- [ ] push your commits in VS Code source control
- [ ] go to your fork on GitHub
- [ ] click Compare & pull request
- [ ] set the base repo to original-owner/repoA and the base branch to main
- [ ] write a description of your changes
- [ ] click Create pull request


### to keep your fork synced with the original punctalyze:
```bash
git remote add upstream https://github.com/ocarmo/punctalyze.git
git fetch upstream
git checkout main
git merge upstream/main
git push origin main
```
🙌 Thanks for using and contributing to punctalyze. Your improvements help make image analysis easier for everyone.

If you have any questions, feel free to open an issue or contact the maintainer.

### if you want to update punctalyze inside your pipeline project, and you're not contributing changes to it, run:
```bash
git submodule update --remote --merge
git commit -am "Update submodule to latest punctalyze commit"
```

### best practices:
organize your repo like this:
```bash
your_project/
├── raw_data/
├── notebooks/
├── src/
│   ├── pre_processing/
│   ├── post_processing/
│   └── your_wrappers.py
├── core_scripts/   ← (Git submodule: punctalyze)
├── README.md
└── environment.yml
```
