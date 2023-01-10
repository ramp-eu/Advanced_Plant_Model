# Advanced Plant Model
  
License: [Copyright © INESC TEC http://www.inesctec.pt 2014-2023. All Rights Reserved.](LICENSE)  
  
User Manual: [pdf](training/APM-BetterFactory-D1_2-2021-Sept.pdf)  
  
Training Material: [files](training)  
  
## Contents

- [Advanced Plant Model](#advanced-plant-model)
  - [Contents](#contents)
  - [Background](#background)
  - [Install](#install)
  - [Usage](#usage)
  - [API](#api)
  - [Testing](#testing)
  - [License](#license)

## Background
  
This repository contains the binary distribution of the APM "Advanced Plant Model", an autonomous software-based system that allows you to build a digital representation of a given manufacturing area, comprising the three-dimensional location, geometry and relationship of key physical elements present in a manufacturing area, such as production lines, workstations, logistic racks and palletes, robotic manipulators, AGVs, and other equipment.  
  
In its most advanced configuration, the APM integrates the Production Manager (PM) element, which controls and monitors the execution of a set of manufacturing activities, scheduled by a MES Manufacturing Execution System, and assigned to the modeled robotic resources. A view of the current state of the manufacturing activities is kept by the APM.  
  
Please note that an instance of the APM is available for each KTE in the RAMP Platform of the BetterFactory project.  If you have a strong reason to deploy a specific instance in your ICT infrastructure, you should follow the instructions below.  
  
The APM is available in executable form and contains all the instructions to install and run it (no need to compile its source code).  
  
## Install
  
The APM is distributed as a docker-based system, intended to be deployed on a Ubuntu Focal 20.04.x LTS system.  
  
1. Install Docker Engine and Docker Compose on Ubuntu 64 bits  
  1.1 Follow the instructions on https://docs.docker.com/install/linux/docker-ce/ubuntu/ to install Docker Engine  
  
2. Install and run the APM  
  The docker files for the APM are available for several configurations, with different sets of data records.  
  There is a 'tar.gz' file for each configuration. For instance, the file 'apm-linux64-4.12.1-docker-betterfactory.tar.gz' contains version '4.12.1' of the APM configured for the environment 'betterfactory'.  
  
  2.1 Copy the available 'apm-linux64-*-docker-*.tar.gz' file to your working directory.  
  2.2 Open a terminal window and expand the tar.gz file.  
  2.3 Change current directory to the one just expanded.  
  2.4 Prepare docker environment (generate docker files):  
         ```docker-compose build```  
      Be patient, several downloads from the network will be done.  
  2.5 Run the APM:  
         ```docker-compose up -d```  
  2.6 Check that the APM is running:  
      (but replace the '<apm>' keyword with the name used in the docker-compose.yml file)  
         ```docker-compose logs -f <apm>```  
      Search for the following two lines:  
        ```[info] - play.api.Play - Application started (Prod)```  
        ```[info] - play.core.server.NettyServer - Listening for HTTP on /0:0:0:0:0:0:0:0:9000```  
  2.7 Open a browser and go to "http://localhost:9000".  
      You get the authentication window from the APM where you are asked to authenticate through one of the following ways:  
        - Login via the RAMP Market place  
        - Login via a GitHub account  
        - Login via a configured email and password (use '@a.a' for the userName and passwd on the 'betterfactory' distribution)  
  
3. Start and stop the APM  
  3.1 Open a terminal window.  
  3.2 Change current directory to the one where you have installed the APM:  
  3.3 To start running the APM:  
         ```docker-compose up -d```  
  3.4 To stop running the APM:  
         ```docker-compose down```  
  3.5 To see the logs of the APM:  
      (butreplace the '<apm>' keyword with the name used in the docker-compose.yml file)  
         ```docker logs -f <apm>```  
  3.6 Other docker-compose commands:  
         ```docker-compose ps```  
         ```docker-compose start```  
         ```docker-compose stop```  
         ```docker-compose restart```  
         ```docker-compose pause```  
         ```docker-compose unpause```  
  
  If you need to reset the build of the APM on the docker, use the command:  
         ```docker-compose build --pull --force-rm```   
  And then follow the normal process:  
         ```docker-compose build```  
         ```docker-compose up -d```  
  
For support please contact Rui Dias (rcdias@inesctec.pt) or César Toscano (ctoscano@inesctec.pt).  
  
## Usage
  
Information about how to use the APM can be found in:  
  - [User Manual](training/APM-BetterFactory-D1_2-2021-Sept.pdf)  
  - [Training - Create Physical Area](training/01-Create-Physical-Area.pdf)  
  - [Training - Implant Objects on the Physical Area](training/02-Implant-Objects-on-the-Physical-Area.pdf)  
  - [Training - Create Physical Area with Map](training/03-Create-Physical-Area-with-Map.pdf)  
  - [Training - Add a new Rack to the Catalogue](training/04-Add-a-new-Rack-to-the-Catalogue.pdf)  
  - [Training - Add a new Rack to the Catalogue with STEP](training/05-Add-a-new-Rack-to-the-Catalogue-with-STEP.pdf)  
  - [Training - Add a new Equipment to the Catalogue](training/06-Add-a-new-Equipment-to-the-Catalogue.pdf)  
  - [Training - Add a new Workstation to the Catalogue](training/07-Add-a-new-Workstation-to-the-Catalogue.pdf)  
  - [Training - Add a new Production Line to the Catalogue](training/08-Add-a-new-Production-Line-to-the-Catalogue.pdf)  
  - [Training - Integration with OPIL, part 1 (Open Platform for Innovations in Logistics)](training/09-Integration-with-OPIL-part-1.pdf)  
  - [Training - Integration with OPIL, part 2 (Open Platform for Innovations in Logistics)](training/10-Integration-with-OPIL-part-2.pdf)  
  
Some brief instructions:  
1. In order to access the APM, you need a browser. Google Chrome and Mozila Firefox are recommended, but you can use other browsers.  
  1.1 If you are running the browser on the same computer that is hosting the APM you should enter the address "http://localhost:9000/".  
  1.2 If you are running the browser on a different computer, you should enter the address "http://name_of_computer_hosting_apm:9000/", where "name_of_computer_hosting_apm" should be replaced with the appropriate values.  
  1.3 If you are using the RAMP Platform, you shoud access the APM on a specific place within RAMP.  
2. The APM supports the creation of users and organizations. However, as this is not important for the moment, you simply enter the email "a@a.a" without password in the login screen.  
3. Having successfully made the login, you get the APM's user interface.  
4. In the "Implantation" area, you find:  
  4.1 The "Set Map": the map of the manufacturing area (you should create a new one and not use the default one).  
  The red symbol defines the point (0,0,0) and two other points specify the horizontal alignment of the map. To specify these two points, press "Set horizontal line" button and click two times on the rebot map. These two points should specify a horizontal line in the map.  
  4.2 The "Set Objects": defines which objects (racks, large boxes) have been created so far and their location in the map (reflecting a given reality).    
  To create an instance of a rack, large box, conveyor or any other object, press the right button on top of a Container Region and select the object to create from the drop down menu. The object will be placed in the middle of the physical area. You may now drag the object to its proper place.  
  Further actions can be made on isolated objects (rack, largeboxe, conveyor, ...) on groups of objects as follows:  
  To select multiple objects, the first object could be selected with or without pressing the Ctrl key. For the remaining objects press the mouse's left hand button on top of the objects together with the Ctrl key (the last object is also selected with mouse's left hand button).  
  Selecting a single object allows you to delete it, to rotate it and to clone it: use the mouse's right hand button to get access to the menu. The clone is created on top of the original object.  
  Selecting multiple objects allows you to delete, rotate and align (vertically, horizontally and orientation) the objects. You can also connect them by a fixed amount.  
  4.3 The "Robots": the identification of all the types of robots the system knows about. You may create a new instance of a robot of a given type.  
  4.4 The "Racks": the identification of all the racks that are implanted in the physical area. Here you can delete any rack.  
  4.5 The "Large boxes and Parts": the identification of all the large boxes that are implanted in the physical area. Here you can delete any large box. For each large box, you can also specify the contained Part.  
  4.6 The "Small boxes and Parts": the identification of all the small boxes that are available in the physical area. Here you can delete any small box. For each small box, you can also specify the contained Part.  
  4.7 The "Conveyors": the identification of all the conveyors that are implanted in the physical area. Here you can delete any conveyor.  
  4.8 The "Kits": the identification of all the kits that were created to support a given Kitting Order. The creation of a kitting order implies the instantiation of a kit (using its configuration).  
5. In the "Type of objects" area, you find information about the types of objects known by the APM: these object types are used to create instances of the corresponding objects (point 4.2 above).  
6. In the "Runtime" area, you have the user interface related to dynamic elements of the APM:  
  6.1 The "World Model" area displays a 3D view of the physical world, i.e., it displays the elements that were implanted in the physical area.  
  6.2 The "Robot fleet" area identifies all known robots.   
  You can also press the "Get Status - TaskManager" button to get the robot status (location) from the OSPS TaskManager.  
  6.3: The "Alerts" area identifies all internal relevant errors and warnings.  

## API
  
Not applicable  
  
## Testing
  
In order to test the APM, you can follow the training material provided on [Usage](#usage).  
  
## License
  
[Copyright © INESC TEC http://www.inesctec.pt 2014-2023. All Rights Reserved.](LICENSE)  
  