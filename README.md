# Infrastructure Automation Testing Using CI/CD Lab

## Introduction: 

In this lab, you will learn to use an  industry-standard pipeline tool, GitHub Actions, to build a simple CI/CD pipeline for testing.  

## Objective

For this lab, you will gain hands-on experience using GitHub Actions for continuous integration and managing your Jenkins configuration
as code.  You will write pipeline jobs using the Groovy DSL and create a GitHub Actions workflow to Build and Test Java code.

## Getting Started:

1. Copy the starter code from here into a new, private repository in your personal GitHub account. When adding a collaborator, be sure to add the instructor ("CSCC-Instructor").

#### The Gradle Project

The source code for this project is quite simple.  It's a simple Java application and a JUnit test suite.  You won't need to change any of its code.  Note that if you want you can build it from the command line with a simple `./gradlew build`

## Completing the Assignment

### Creating a New Branch
1. At the top of your repo, select the drop down that says "main"
1. In the field that says "Find or create a branch..." type "assignment", then select the item that says "Create branch: assignment from 'main'"

**Note:** Your repository should automatically switch to this new branch

You are now ready to add your workflow.

### Creating GitHub Actions Workflow: 

For this lab you will create a GitHub Actions workflow that will execute a pipeline job that will do 3 things. Your workflow should run when something is pushed and when a pull request is made:
1. Checkout _your_ repository in a container using the latest version of Ubuntu (Linux)
1. Build the source code using Gradle and upload the executable JAR file to the build summary
1. Report the unit test results by uploading the test report as a zip archive

## Hints
1. Refer to the previous lab which demonstrates how to properly create a Ubuntu container, checkout the code in this repository, then build the Gradle project.
1. The keywords to run the workflow 'on' are:
   * `push` and `pull_request`
1. You will uses the action `actions/upload-artifact@v3` in order to add artifacts (JAR and Test Reports) to the workflow summary. This is the basic outline of what this will look like, you will need to fill in the information next to the keywords:

```
    - uses: actions/upload-artifact@v3
      with:
        name:
        path:
```

**Note**: You will need two instances of this job, one for the build JAR and the other for the Test Report.

## Submitting Your Work

1. Publish your repository as a private repo, and ensure that you have pushed the latest version
1. Open a pull request from your branch to master and assign your instructor as a reviewer
1. Download the JAR and Test Report by going to your workflow summary clicking on the items under the `Artifacts` section
   * Ensure that the correct files are included in each zip archive. You can check this by running `./gradlew build` in your intelliJ IDE terminal and then navigating to the `build` folder then comparing the contents in your zip archives.
1. Submit the assignment in Blackboard and attach both archives, one with the JAR file and one with the report.

__NOTE: Feedback will be given via. comments in your pull request.__
