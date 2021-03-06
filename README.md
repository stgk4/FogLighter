# FogLighter (A Maven Archetype for FogLight projects)

## What you will need before you start:
#### [Java 8](https://docs.oracle.com/javase/8/docs/technotes/guides/install/install_overview.html) 
#### [Maven](https://maven.apache.org/install.html)
,which downloads and manages the libraries and APIs needed to get the Grove device working.
#### [Git](https://git-scm.com/)
, which clones a template Maven project with the necessary dependencies already set up.
#### [PuTTY](http://www.putty.org/)
, which allows you to interact and control your device

## Starting Your Own Project

 In the command line or terminal of your local machine, enter:
```
 git clone https://github.com/oci-pronghorn/FogLighter.git
 cd FogLighter
 mvn install
 ```
 
Now, ```cd``` into a directory that you would like your own IoT project to be created in, and enter:
```
mvn archetype:generate -DarchetypeGroupId=com.ociweb -DarchetypeArtifactId=FogLight-Archetype -DarchetypeVersion=0.1.0-SNAPSHOT
```
The terminal now asks for:

```groupID```: type in  *com.ociweb* then press Enter

```ArtifactID```: type in name of your project (with no spaces) then press Enter

```version: 1.0-SNAPSHOT ```: Ignore, Press Enter

```package: com.ociweb ```: Ignore, Press Enter

```Y:```  :  Type *Y*, press Enter


This will create a folder named after your project, which includes all the project files. Let’s call our project *ProjectXYZ*.  
If you’re working from Terminal, open up the file  “ProjectXYZ”/src/main/java/com/ociweb/IoTApp.java . You can start implementing the project code from here. 

If you’re using an IDE, open up the created Maven project - *ProjectXYZ* and start working from IoTApp.java
 
### Importing the Maven project in Eclipse
Select File -> Import

Click on "Exisiting Maven Projects" under Maven, then click "Next"

Click "Browse" and select the directory (folder) under your project that contains the "src" folder as well as a "pom.xml" 
file.

Click "finish"

### Importing the Maven project in NetBeans 
Select File -> Open Project

Click "Browse" and select the directory (folder) under your project that contains the "src" folder as well as a "pom.xml" 
file.

Click "Open Project"

Note: In Netbeans, instead of typing ```mvn install```, you can also build your project by clicking "Build".

### Importing the Maven project in IntelliJ
Select File -> Open.

Click "Browse" and select the directory (folder) under your project that contains the "src" folder as well as a "pom.xml" 
file.

Click "OK".

The import will be performed automatically.

### Building the project
Open your project folder in the terminal of your choosing and type
```
mvn install
```
.. to build the project. This will create a .jar file named ProjectXYZ.jar in the **/target** folder (note that there are other .jar files  in **/target**, but we don’t have to worry about those). This jar is executable and contains all its needed dependencies. 

### Importing and running the project to your device
After succesfully building the project, ```cd``` into the **/target** folder. Now, use 
```
scp ProjectXYZ.jar username@servername:
``` 
This will send the jar file to your RaspberryPi. You can also send the jar file to a specifc location by adding the file path after the colon. For example, if your username was "pi", the server name was "raspberry" and you wanted to add the .jar file to your Projects folder, the command would look like this ..
```
scp ProjectXYZ.jar pi@raspberry:/Projects/
```

Once the project is your device, use PuTTY to connect to your device. In PuTTY, if needed, ```cd``` into the folder containging your .jar file and then use the following command on your device..
```
java -jar ProjectXYZ.jar
```
.. to execute it. To exit the app at any time, press Ctrl+c.


