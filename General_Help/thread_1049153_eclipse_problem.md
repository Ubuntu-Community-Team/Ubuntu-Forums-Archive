---
title: "eclipse problem"
date: 2009-01-24
forum: General Help
---

### Post by Despot Despondency on 2009-01-24
I'm having problems running a program in eclipse. The program opens up a involves opening up a JFrame with a picture in the background. When I run the program in eclipse the JFrame opens, but it is blank and then goes gray and crashes. It's not the program itself because I can run it perfectly from the terminal, so it seems to be eclipse. 

Has anyone else had this problem, or know how to resolve it?

---

### Post by Despot Despondency on 2009-01-27
Bump, bump, ba da bump.

---

### Post by jespdj on 2009-01-27
Which version of Java are you using? I recall that with some versions of Java (for example, Sun Java 5) there were problems with Swing and Compiz, which could lead to symptoms like you describe.

Install the latest Sun Java 6:
```
sudo apt-get install sun-java6-jdk
```
and make sure that that's the Java version that's used:
```
sudo update-alternatives --config java
```
Also check your Eclipse project settings so that it's using Sun Java 6 to run your program.

---

### Post by theApokalypsis on 2009-01-27
ya I had some issues with my jre as well; jespdj gots you on the right path :). I usually went for Sun's version, and not the openJDK. I was using Eclipse (3.4) (Ganymede) with Compiz and found it worked best.

---

### Post by Despot Despondency on 2009-01-27
Cool, thanks for the help. That seemed to do the trick.

---

