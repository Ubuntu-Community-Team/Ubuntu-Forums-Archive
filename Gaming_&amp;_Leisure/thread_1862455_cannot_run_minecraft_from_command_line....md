---
title: "cannot run minecraft from command line..."
date: 2011-10-16
forum: Gaming &amp; Leisure
---

### Post by ELD on 2011-10-16
Okay so i am on nvidia optimus and i have installed bumblebee to be able to actually use my nvidia card.

Problem is to do it i need to run the command "optirun" before everything. So in terminal:
"optirun <somegame>" for example to use the nvidia card instead of the intel one.

My question is: How do i run minecraft correctly via terminal? It's a java file.

---

### Post by 7cardcha on 2011-10-16
This is easy :D 
1. Open up a terminal
2. install java(If you have java skip this)by typing sudo apt-get install sun-java6-jre
3. type java -jar /path/to/your/minecraft.jar (You will need to replace that last part with the path to your minecraft.jar For example if you downloaded it to your Downloads folder and your username was joe it would be java -jar /home/joe/Downloads/minecraft.jar)
4. If you have problems ask.

---

### Post by ELD on 2011-10-17
Problem is running it via terminal gives errors, where as running it directly it opens fine ??

> 
liam@liam-Ideapad-Z570:~/Downloads$ java -jar '/home/liam/Downloads/minecraft.jar' 
Exception in thread "main" java.awt.HeadlessException
    at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:173)
    at java.awt.Window.<init>(Window.java:476)
    at java.awt.Frame.<init>(Frame.java:419)
    at net.minecraft.LauncherFrame.<init>(LauncherFrame.java:27)
    at net.minecraft.LauncherFrame.main(LauncherFrame.java:158)
    at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:13)



---

### Post by 7cardcha on 2011-10-17
Do you have more than 1 version of java installed?

---

### Post by ELD on 2011-10-17
Originally yes but now only sun java 6.

---

### Post by 7cardcha on 2011-10-17
OH I REMEMBER I had this problem before reinstalling MC did nothing. I forgot what the solution was. Give me a minute to remember.

---

### Post by ELD on 2011-10-18
Any idea?

---

### Post by proteusmoteus on 2011-10-26
Do 'java -version' and confirm your java is sun.

If java is still pointing at openjdk despite being uninstalled launch sun java via
/usr/lib/jvm/java-6-sun/bin/java

---

### Post by ELD on 2011-10-26
> **proteusmoteus said:**
> Do 'java -version' and confirm your java is sun.

If java is still pointing at openjdk despite being uninstalled launch sun java via
/usr/lib/jvm/java-6-sun/bin/java

Ideal you have my thanks, i just need to set sun java as the default.

---

