---
title: "How to run a Java application"
date: 2009-04-25
forum: General Help
---

### Post by pete-soper on 2009-04-25
Hi,

I am trying to run a java application that runs quite happily under windows in Ubuntu (Hardy Heron), to stop having to switch back into windows.

In windows, it is executed using a batch file that contains:

@echo off 
java -Xmx500m -cp .;Theme.jar Gui

I can see thar Theme.jar is a file in the folder, but not Xmx500m

I have no idea how to get this to run. I have tried ./Theme.jar and get 'insufficient access'. If I try sudo first, I get 'no such file'. Any help would be much appreciated.

Pete

---

### Post by conscious on 2009-04-25
Try something like
```
java -jar Theme.jar Gui
```
or
```
java -Xmx500m -cp . -jar Theme.jar Gui
```
-Xmx500m, in fact, is not a reference to a file, it allocates 500 Mb of memory for your application.

---

### Post by pete-soper on 2009-04-25
That looks like its getting me closer. I now get "Failed to load Main-Class manifest attribute from Theme.jar".

Any further suggestions??

Thanks in advance,

Pete

---

### Post by conscious on 2009-04-26
Some people seem to have had this problem, and solved it by using Sun's JRE, see e.g. [http://getsatisfaction.com/wuala/topics/failed_to_load_main_class_manifest_attribute](http://getsatisfaction.com/wuala/topics/failed_to_load_main_class_manifest_attribute)

---

### Post by pete-soper on 2009-05-04
It appears that I am using the Sun JRE.
This is the result of the alternative configure

update-alternatives --config java

There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.

Having checked the -cp option, I have double checked that I am executing the command in the same directory as the 'Theme.jar'.

java -Xmx500m -cp . -jar Theme.jar Gui
Any other ideas would be welcomed?

---

### Post by gamblor01 on 2009-05-04
> 
In windows, it is executed using a batch file that contains:

@echo off 
java -Xmx500m -cp .;Theme.jar Gui
Yep, it would be executed that way in Windows.  However, in Linux the semicolon character is used to separate commands.  You can type multiple commands into the terminal all separated by semicolons and they will execute one after the other (with no regard to whether or not the previous command executed successfully, but that's a different topic).  Suppose you type the following

cd ~; ls; cd /; ls

It should cd into your home directory, then list the files, then cd into the root directory, and then list the files, as if you had typed the four commands separately.  So that's the problem.  The -cp option to java (classpath) has a semicolon in it which causes the shell to interpret this as 2 separate commands, as if you had typed them separately in the terminal like so:

```

$ java -Xmx500m -cp .
$ Theme.jar GUI

```Make sure that the Theme.jar and Gui.class files are both in the same directory, and then change the semicolon to a colon and try to launch the file like this:

```

java -Xmx500m -cp .:Theme.jar Gui

```It should work.  Basically, all it's doing is telling Java to execute the program named Gui with the following options:

**-Xmx500m**
sets the maximum heap size to 500 megabytes

**-cp .:Theme.jar**
tells Java to include some extra files in the classpath, namely, any file that exists in the current directory (referenced by . [dot]) as well as the classes that exist inside of Theme.jar



This should work...let me know if it doesn't.

---

### Post by pete-soper on 2009-05-05
Brilliant, you've cracked it. With help from this forum and Ri my resident Ubuntu guru the application is now running. 

Thanks for your help. 

Pete

---

### Post by gamblor01 on 2009-05-05
Glad to help.  Sorry it took a week to solve this one, but I just joined the forums like 2 or 3 days ago so I answered as quickly as I could.  ;)

---

