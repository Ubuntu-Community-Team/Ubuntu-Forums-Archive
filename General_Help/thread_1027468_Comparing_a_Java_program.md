---
title: "Comparing a Java program"
date: 2009-01-01
forum: General Help
---

### Post by vitaminz on 2009-01-01
Hi, for a University coursework I have the task of comparing Ubuntu and Windows, and part of the coursework requires us to compare how a program runs on both Windows and Ubuntu, and I decided to use Java for this, as I don't have any knowledge in C or the like.

However I'm having problems actually getting Java to run on Linux - I downloaded the binary files but how do I go about extracting them? The Java manual for this just says 'extract the files'.

Or is there a simpler way/easier way to run a Java program on Linux?

Thanks :)

---

### Post by taurus on 2009-01-01
You can install java from the repos.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
When you get to the java license screen, press the Tab key to highlight the <OK> and Return to accept it.

Now, you can check to make sure you have the right version.

```
java -version
```

---

