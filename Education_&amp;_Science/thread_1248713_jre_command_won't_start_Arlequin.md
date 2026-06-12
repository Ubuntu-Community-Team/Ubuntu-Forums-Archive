---
title: "jre command won't start Arlequin"
date: 2009-08-24
forum: Education &amp; Science
---

### Post by spinoza666 on 2009-08-24
Hey people,

I've just downloaded and untarred the population genetics package Arlequin. It is supposed to be started using the jre command, and although I've installed sun-java6-jre, it will not start. It's basically a folder with a script I believe (arlequin.bat), which you are supposed to run. This file is executable, but when I run the command (jre -cp arlequin.jar -cp swingall.jar arlequin.ArlequinApp) within the folder, it says that this is an unknown command. Does anybody know which package includes this command, or am I doing something else wrong?

-Atle

---

### Post by machoo02 on 2009-08-25
Perhaps try:[PHP]java -jar arlequin.jar[/PHP]

BTW, the newer version of Arlequin (3.11) works great under Wine.

---

### Post by DaithiF on 2009-08-25
Hi,
similar to machoo02's response, but I would try the original command but with java:
```
java -cp arlequin.jar -cp swingall.jar arlequin.ArlequinApp
```JRE = Java Runtime Environment = the collection of executables & libraries which allow you to run java programs, but java is the actual name of the executable you need to run.  Installing a JRE gives you (among other things), an executable called java.

I'm a little doubtful too about the two separate -cp (classpath) parameters.  I've never seen that before, usually you would a single -cp parameter with components separated by ':', like:
```
java -cp arlequin.jar:swingall.jar arlequin.ArlequinApp
```so try this is the first command doesn't work.

---

### Post by spinoza666 on 2009-08-25
Thanx for your responses:)

But sad to say it still doesn't work, while I do get some java related messages now. 

I'm starting to think that I've done the wrong install. There's two ways of installing. One where you just untarr Arlequin itself (arlequin20.tar.gz), and another where you untarr Arlequin and JRE (arlequin20_jre.tar), which includes jre_glibc.tar.gz and  arlequin20.tar.gz. The former you're supposed to decompress in /usr/local, while the latter should be untarred where ever, and then double-click arlequin.bat to run.

I opted for only untarring arlequin20.tar.gz as I already have sun-java6-jre installed, and do not want to mess with it frankly. Should I perhaps try the other option of installing both?

Any advice would be much appreciated:)

---

### Post by DaithiF on 2009-08-25
can you paste the output that you get here.
thanks

---

### Post by spinoza666 on 2009-08-25
Cool:)

Here goes.

Command from Arlequin website:
```
jre -cp arlequin.jar -cp swingall.jar arlequin.ArlequinApp

```
Gives the following output:
```
bash: jre: command not found
```

While:
```
java -jar arlequin.jar 
```
produces this:
```
Failed to load Main-Class manifest attribute from
arlequin.jar
```

and this
```
java -cp arlequin.jar -cp swingall.jar arlequin.ArlequinApp
```
produces this:
```
Exception in thread "main" java.lang.NoClassDefFoundError: arlequin/ArlequinApp
Caused by: java.lang.ClassNotFoundException: arlequin.ArlequinApp
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: arlequin.ArlequinApp.  Program will exit.
```

and eventually this:
```
java -cp arlequin.jar;swingall.jar arlequin.ArlequinApp
```
outputs this:
```
Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)

where options include:
    -d32          use a 32-bit data model if available

    -d64          use a 64-bit data model if available
    -client	  to select the "client" VM
    -server	  to select the "server" VM
    -hotspot	  is a synonym for the "client" VM  [deprecated]
                  The default VM is server, 
                  because you are running on a server-class machine.

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
                  load native agent library <libname>, e.g. -agentlib:hprof
                    see also, -agentlib:jdwp=help and -agentlib:hprof=help
    -agentpath:<pathname>[=<options>]
                  load native agent library by full pathname
    -javaagent:<jarpath>[=<options>]
                  load Java programming language agent, see java.lang.instrument
    -splash:<imagepath>
                  show splash screen with specified image
bash: swingall.jar: command not found

```

I do have some java experience, but this is beyond my meagre skills.

---

### Post by DaithiF on 2009-08-25
hmm, well some things are for sure...
1. your existing java DEFINITELY won't work.  This thing requires a version of java which is 10 years old !
2. Even downloading the 10-year old jre that they bundle with the app, I still can't get it to work -- it references RedHat6 in its Linux installation instructions -- the world has moved on **a lot** since RedHat 6, and despite patching a number of issues (it requires an arch script that isn't present on ubuntu, it uses a non-existing -p parameter for dirname, etc) the end result for me after all this was a Segfault.

So basically this program as supplied isn't compatible with linux.  Maybe the previous posters suggestion of running the newer version under Wine may be the way to go.

---

### Post by spinoza666 on 2009-08-26
Doh!

Yeah that Red Hat comment threw me off a bit as well:) 

I have done my best to stay away from Wine, but now it seems the time as come for me to bite the bullet....

Anyway, thanks a bunch for clearing this up for me. Don't be surprised if you receive a thank you in my thesis, if I ever get to finish it:)

---

### Post by machoo02 on 2009-08-26
I had asked about a Linux version of Arlequin a while ago on the old Genetic Software Forum hosted by B. Rannala, but I never really got a reply.  Probably not too high on Excoffier's to-do list.  

The newer version of Genepop works really well natively, and I've also had success with running FSTAT through Wine as well.  Feel free to send any more questions.  Good luck finishing your thesis...I'm turning my dissertation in to my committee on Friday.  \o/

---

