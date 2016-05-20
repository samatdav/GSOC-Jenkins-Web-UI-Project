# GSOC Jenkins Web UI Project

#### Here is my current progress

**May 20** - At this point I talked with several mentors and discussed possible approaches to my projects. I installed Jenkins on my Ubuntu machine and now can make changes and run them by *mvn jenkins-dev:run*. 
With mentors we mostly discussed new job creation project and in particular popup window. That should require 3 steps: rendering popup, receiving JSON with job types, and sending POST request to create the job. I found [newJob.jelly](https://github.com/jenkinsci/jenkins/blob/master/core/src/main/resources/hudson/model/View/newJob.jelly) file which should be the starting point in doing the popup.
Now, I am trying to do a better job name validation first. I am changing [add-item.js](https://github.com/jenkinsci/jenkins/blob/master/war/src/main/js/add-item.js) and try to get some new functions. I try to send a GET request after each character typed. Although I understand how the file works and what changes to do, it does not work yet. Hopefully, I will fix it in a day or two. 
After finishing name validation I plan to start creating new job popup window. All three steps do not sound difficult to me by themselves. However, I feel like the main challenge could be understanding of structure of Jenkins and integration of changes there.

#### Here is my plan from proposal with updates in new job creation project.

1. **New job creation**
* [Required] New job name validation
    * Sending GET request to doCheckJobName after each input character
    * Blocking item creation if it’s name is inappropriate
* [Required] Popup window. [Here is a demonstrating animation](http://i.imgur.com/6O3jcuA.gif)
    * Rendering a popup window with job creation    
    * Receiving JSON with job types
    * Sending a POST request with job name and type
* [Optional] Simple new job configuration
    * Job creation popup contains step to preset some of configuration
    * Job creation popup sends a POST request to change confuguration on job creation
2. **Configuration page**
* [Required] Changing help information. [Here is a demonstrating animation.](http://i.imgur.com/zoSvB1G.gif)
    * The extension points and the plugin using them are created
    * Help information can be styled using markdown
    * Admin can choose editing rights to deny or allow users to modify the help
    * [Optional] The functionality is extended to creation of crowd sourced "wiki like" documentation. As in [localization plugin](https://wiki.jenkins-ci.org/display/JENKINS/Translation+Assistance+Plugin) the changes are gathered and applied beyond installation of a particular user
* [Required] More intuitive configuration page. Pursuing to solve [this issue](https://issues.jenkins-ci.org/browse/JENKINS-32578)
    * Accordion based navigation with collapsable parts
    * Configuration finder autocomplete
3. **Home page**
* [Optional] Removing "My Views" page. [Here is a demonstrating image.](http://i.imgur.com/Dk8E5I4.jpg)
    * "My Views" tabs are moved to home page
    * Icons are added to "My Views" tabs
    * View creation page functionality can create either of the types
* [Optional] Reducing number of UI elements
    * Elements "enable auto refresh", “edit description”, “icon sizes”,”legend”, “RSS” are removed from home page
    * The elements are placed under "Manage Jenkins" or an upper menu
    * New extension points are created to support new UI elements through plugins
4. **Credentials store page**
* [Optional] Grouping credentials and their domains. [Here is a demonstrating image.](http://i.imgur.com/BUTVU5d.jpg)
    * Credentials are shown under corresponding domains on one page
    * Domains may be added, configured, or deleted on this page
    * Credentials may be added, configured, or deleted on this page
