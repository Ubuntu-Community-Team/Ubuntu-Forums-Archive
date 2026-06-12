---
title: "How to Install Kiba Dock"
date: 2007-09-25
forum: Desktop Effects &amp; Customization
---

### Post by mlyons16 on 2007-09-25
Good day, I'm looking for an easy way to install Kiba dock. I've done some Google searching but it doesn't seem to be very clear. I'm looking for a step by step installation guide here. I'm fairly new to Ubuntu but I've been getting very familiar with it.

Can someone help me?

---

### Post by gsiliceo on 2007-09-26
Go to this thread
[http://ubuntuforums.org/showthread.php?t=268645](http://ubuntuforums.org/showthread.php?t=268645)

---

### Post by mlyons16 on 2007-09-26
Alright, I checked out that link. Where do I start? I don't get it. Sorry!

---

### Post by unabatedshagie on 2007-09-26
The easiest way would probably be to add Treviño&#8217;s repository.

To do this open the terminal and type in **sudo gedit /etc/apt/sources.list** and paste the following at the bottom of it ```
[FONT=courier new,courier] # Treviño&#8217;s Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
 # Many eyecandy 3D apps like Beryl, compiz and kiba-dock snapshots
 # built using latest available (working) sources from git/svn/cvs&#8230;
 deb http://download.tuxfamily.org/3v1deb feisty eyecandy
 deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy[/FONT]
```[FONT=courier new,courier]Save and exit gedit and now copy and paste the following into the terminal to download the key to authenticate the packages[/FONT]```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```Now in the terminal type **sudo apt-get update** then **sudo apt-get install kiba-dock** and that should do it.

---

### Post by mlyons16 on 2007-09-26
cool, I'll give that a try tonight when I get home. If I don't experience any success, I'll be back! Thanks though.

---

