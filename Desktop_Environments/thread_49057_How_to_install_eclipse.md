---
title: "How to install eclipse?"
date: 2005-07-14
forum: Desktop Environments
---

### Post by liminal on 2005-07-14
Hi, I'm new to linux and would like to install the eclipse java developing environment.

I downloaded eclipse-SDK-3.1-linux-gtk.tar.gz from the website. What do I do with it? Where should it be unpacked?

Also, won't it expect me to have java installed? Do I have java installed? Where should I look to check?

Thank you and sorry for the newbie questions.

---

### Post by dave9191 on 2005-07-14
Unpack it where you like, I put it in /opt. You'll have to use sudo or a root file manager window. 

You need java installed. Try typing java and javac into a command line console to see if you have them. If not you will need to install it. There is a nice section in the ubuntu wiki about it from what i remember. 

Then to run eclipse run the bin file in the directory that you unpacked it. When first run it should ask you where the JVM is / give you a choice. If it doesnt start up properly you will need to tell it where it is in the command line used to start the program. How to do that can be found in the eclipse readme file. 

Once you get it running make an icon for it that has the location of the bin file and any command line parameters it needs. 

Dave

---

### Post by liminal on 2005-07-14
Thanks dave9191,

I found information on how to install java, but that looks like a whole other set of things to learn...

---

### Post by byen on 2005-07-14
[QUOTE=dave9191]
You need java installed. Try typing java and javac into a command line console to see if you have them. 
Dave[/QUOTE]

sorry for the intrusion, but i was about to post the same Q in a few minutes..well..i typed java in the terminal as suggested and i get :

byen@ubuntu:~$ java
Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)

where options include:
    -d32          use a 32-bit data model if available

    -d64          use a 64-bit data model if available
    -client       to select the "client" VM
    -server       to select the "server" VM
    -hotspot      is a synonym for the "client" VM  [deprecated]
                  The default VM is client.

    -cp <class search path of directories and zip/jar files>
    -classpath <class search path of directories and zip/jar files>
                  A : separated list of directories, JAR archives,
                  and ZIP archives to search for class files.
    -D<name>=<value>
                  set a system property
    -verbose[:class|gc|jni]
                  enable verbose output
    -version      print product version and exit
    -version:<value>
                  require the specified version to run
    -showversion  print product version and continue
    -jre-restrict-search | -jre-no-restrict-search
                  include/exclude user private JREs in the version search
    -? -help      print this help message
    -X            print help on non-standard options
    -ea[:<packagename>...|:<classname>]
    -enableassertions[:<packagename>...|:<classname>]
                  enable assertions
    -da[:<packagename>...|:<classname>]
    -disableassertions[:<packagename>...|:<classname>]
                  disable assertions
    -esa | -enablesystemassertions
                  enable system assertions
    -dsa | -disablesystemassertions
                  disable system assertions
    -agentlib:<libname>[=<options>]
                  load native agent library <libname>, e.g. -agentlib:hprof                    see also, -agentlib:jdwp=help and -agentlib:hprof=help    -agentpath:<pathname>[=<options>]
                  load native agent library by full pathname
    -javaagent:<jarpath>[=<options>]
                  load Java programming language agent, see java.lang.instrument

______________________________________________________________________________________

---

### Post by dave9191 on 2005-07-15
[QUOTE=byen]sorry for the intrusion, but i was about to post the same Q in a few minutes..well..i typed java in the terminal as suggested and i get :

byen@ubuntu:~$ java
Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)
______________________________________________________________________________________[/QUOTE]


If you get that output it means that java is installed. Otherwise it would say that command isnt found. Also make sure that you have javac, to make sure you have the SDK intsalled, not just the virtual machine. So that eclipse will be able to complile porgrams :) 

Dave

---

### Post by byen on 2005-07-15
ok so java is installed! phew...no how to I get about doing javac and eclipse. i tried typing javac on the terminal to see if it was there..but says command not found..so im assuming javac is not there.... please suggest.
thank you for the time...

---

### Post by dave9191 on 2005-07-15
have you read the many guides about installing java? There are guides at the sun site as well. Or you can apt-get it from the repositories. 

sun-j2re1.5 - Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)
sun-j2sdk1.5 - Java(TM) 2 SDK, Standard Edition, Sun Microsystems(TM)

sudo apt-get install sun-j2sdk1.5

Dave

---

### Post by byen on 2005-07-16
[QUOTE=dave9191]have you read the many guides about installing java? There are guides at the sun site as well. Or you can apt-get it from the repositories. 

sun-j2re1.5 - Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)
sun-j2sdk1.5 - Java(TM) 2 SDK, Standard Edition, Sun Microsystems(TM)

sudo apt-get install sun-j2sdk1.5

Dave[/QUOTE]
 got em using apt-get. Sorry, I know i should have looked around.... Will make it a point to do so from now! thanks!

---

