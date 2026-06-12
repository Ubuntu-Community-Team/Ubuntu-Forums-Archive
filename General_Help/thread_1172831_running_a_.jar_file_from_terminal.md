---
title: "running a .jar file from terminal"
date: 2009-05-29
forum: General Help
---

### Post by Fred Bear on 2009-05-29
I am at my total wits end!  I looked all throughout this forum & on Google to find a way to run a .jar file from the terminal.  And yes, I tried 'java -jar /path/to/file' ad nauseum but all I get is the error message, "Unable to access jarfile name_of_jar_file.jar."  And yes, I have Sun Java installed.  In fact, I have both Sun Java 5 & 6 installed onto my system.  I have no problem at all running the .jar file if I open up nautilus and double-click on the file.  Why in the hell does something that should be soooooooo simple practically require someone with brain surgeon type expertise!?  In Windows, I can open up an MSDOS window and open a file from there just by typing in the path to the file that I wish to open and then pressing enter.  Simple!  Shouldn't the system, which knows what the default application is for running files of that type, know all by itself just how to open the file and then open the file?  It's this type of stuff that keeps Linux from getting more users!](*,)

---

### Post by kpkeerthi on 2009-05-29
Which of those Sun's Java is set as default in your PC? Post the output of
```
java -version
```

---

### Post by Fred Bear on 2009-05-29
Here is the output of that terminal command, kind sir:

java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

Thank-you for your prompt reply!

---

### Post by QIII on 2009-05-29
The "Unable to access..." message indicates that the .jar you referenced doesn't exist, not that is won't run.  When you double click from nautilus, you are actually looking at something that definitely exists.

I do a lot of development in Java.

I am consistently frustrated by the fact that I sometimes can't get my apps to run from the terminal -- until I realize that I have either capitalized something, not capitalized something, incorrectly entered the path, or have misspelled something.  java -jar /foo/bar/this.jar  <>  java -jar /foo/bar/This.jar   That sort of thing.

I hate to ask the obvious, but:  Have you double checked the path (really!), the spelling, capitalization, etc?

---

### Post by Fred Bear on 2009-05-29
You know what, I feel like smacking myself bigtime!!!  See, the file I typed in the terminal was frozenbubble.jar when it actually was frozenBubble.jar!  Damn, I feel sooooo stupid!  I am sorry for creating such a commotion!  Thank you very very much for pointing that out to me!!!

---

### Post by kpkeerthi on 2009-05-29
Use tab auto completion for file name. Just type a few chars of a file and press the [TAB] key. Bash will auto-complete the file name if it found a match. Press the [TAB] key again to see all possible matches

```

java -jar froze[TAB]

```

---

### Post by colau on 2009-05-29
> **Fred Bear said:**
> I am at my total wits end!  I looked all throughout this forum & on Google to find a way to run a .jar file from the terminal.  And yes, I tried 'java -jar /path/to/file' ad nauseum but all I get is the error message, "Unable to access jarfile name_of_jar_file.jar."  And yes, I have Sun Java installed.  In fact, I have both Sun Java 5 & 6 installed onto my system.  I have no problem at all running the .jar file if I open up nautilus and double-click on the file.  Why in the hell does something that should be soooooooo simple practically require someone with brain surgeon type expertise!?  In Windows, I can open up an MSDOS window and open a file from there just by typing in the path to the file that I wish to open and then pressing enter.  Simple!  Shouldn't the system, which knows what the default application is for running files of that type, know all by itself just how to open the file and then open the file?  It's this type of stuff that keeps Linux from getting more users!](*,)
[http://worldforum.pardus-linux.nl/index.php?topic=1772.0](http://worldforum.pardus-linux.nl/index.php?topic=1772.0)

---

### Post by Soul-Sing on 2009-05-29
> **Fred Bear said:**
> I am at my total wits end!  I looked all throughout this forum & on Google to find a way to run a .jar file from the terminal.  And yes, I tried 'java -jar /path/to/file' ad nauseum but all I get is the error message, "Unable to access jarfile name_of_jar_file.jar."  And yes, I have Sun Java installed.  In fact, I have both Sun Java 5 & 6 installed onto my system.  I have no problem at all running the .jar file if I open up nautilus and double-click on the file.  Why in the hell does something that should be soooooooo simple practically require someone with brain surgeon type expertise!?  In Windows, I can open up an MSDOS window and open a file from there just by typing in the path to the file that I wish to open and then pressing enter.  Simple!  Shouldn't the system, which knows what the default application is for running files of that type, know all by itself just how to open the file and then open the file?  It's this type of stuff that keeps Linux from getting more users!](*,)

+1 cant run Jar files here....

---

