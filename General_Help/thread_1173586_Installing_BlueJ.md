---
title: "Installing BlueJ"
date: 2009-05-29
forum: General Help
---

### Post by ThewhiteLynx on 2009-05-29
how do I install this Text editor for java named BlueJ, I have tried the install instructions on their website (bluej.org); however, I found that there are better instructions on another rather out of date ubuntu thread [http://ubuntuforums.org/showthread.php?t=148758](http://ubuntuforums.org/showthread.php?t=148758)
however once I get to the point where I should enter
sudo java -jar bluej-251.jar
it says, "sudo: java: command not found."
I looked in the directory and there is "java.exe" in the folder, so why is it giving the error?

---

### Post by doas777 on 2009-05-29
assuming you have a jdk installed, the easiest way to fix this is to rerun the install script. it will ask you were your jdk is located. you can set it manually in ~/bluej/bluej.

when you installed it, did a jdk version show up in the configuration window?

also what jdk do you have? if you don't know, run:
```

javac -version

```and post the output.

if you don;t have a jdk you can install it with:
```
sudo apt-get install **sun-java6-jdk**
```

---

### Post by ThewhiteLynx on 2009-05-30
I have JDK6 update 14, I just installed it a few hours ago.
I tried to run sudo apt-get install sun-java6-jdk however I get the error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jdk: Depends: sun-java6-bin (= 6-13-1) but it is not going to be installed
  sun-java6-jre: Depends: sun-java6-bin (= 6-13-1) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-13-1) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
thewhitelynx@thewhitelynx-desktop:/$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
thewhitelynx@thewhitelynx-desktop:/$

---

### Post by doas777 on 2009-05-30
> **ThewhiteLynx said:**
> I have JDK6 update 14, I just installed it a few hours ago.
I tried to run sudo apt-get install sun-java6-jdk however I get the error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jdk: Depends: sun-java6-bin (= 6-13-1) but it is not going to be installed
  sun-java6-jre: Depends: sun-java6-bin (= 6-13-1) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-13-1) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
thewhitelynx@thewhitelynx-desktop:/$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
thewhitelynx@thewhitelynx-desktop:/$

well i don't like the look of that error but if you believe you have the jdk installed, what do you have in your ~/bluej/bluej file?

---

### Post by ThewhiteLynx on 2009-05-30
I didn't have a bluej file because the installer failed... however the odd thing is I just tried it one last time and it appears to work fine now.  

Thanks

---

