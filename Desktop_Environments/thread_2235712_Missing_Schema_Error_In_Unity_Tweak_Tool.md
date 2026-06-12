---
title: "Missing Schema Error In Unity Tweak Tool?"
date: 2014-07-22
forum: Desktop Environments
---

### Post by bratromas on 2014-07-22
Hello, I am new to Ubuntu and, naturally, have been tinkering around with everything. I love Ubuntu 14.04, but I may have been a little careless while trying to make everything perfect. I just switched over from the KDE version of OpenSUSE, and was getting my Unity desktop to my liking until Unity Tweak Tool stopped working for some reason. I believe it's because I decided that I wanted to try Gnome 3 since the last few updates and mindlessly deleted some dependencies when I realized that I still didn't like it and removed it. 

When I try to run Unity Tweak Tool, I get the following error:

```
$ unity-tweak-tool
Error: schema com.canonical.indicator.appmenu.hud not installed
```

I then tried to install the package needed, assuming it was accidentally deleted with:

```
$ sudo apt-get install indicator-appmenu
```

However, after reading the package lists and trying to install, the terminal reads back: 

```
indicator-appmenu is already the newest version.
``` 

If anyone needs more information, please let me know. I understand that I didn't provide too much, but I have no idea about what else to provide.

Thanks ahead of time, and thanks for taking an interest in this thread. :)

---

### Post by Frogs Hair on 2014-07-22
Hello and Welcome 

Try the following command to make sure you have all the Ubuntu desktop dependencies .```
 sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by bratromas on 2014-07-22
First off, thank you for the reply and for being so welcoming. I tried the command and it didn't install any new packages for me. I guess I have all of the dependencies.  I tried installing Gnome again earlier today and re-installed the Unity Tweak Tool, but I still have no avail. Maybe it's just a bug. Would you like me to try anything else, or should I go ahead and file a bug report?

---

### Post by Frogs Hair on 2014-07-22
Installing or removing  Gnome shouldn't affect the Tweak Tool if it was from the software center, however if it was from a ppa then there could be dependency issues . The Gnome Shell has the Gnome Tweak tool and is specific to the shell and UT is specific to Unity.

---

### Post by bratromas on 2014-07-22
> **Frogs Hair said:**
> Installing or removing  Gnome shouldn't affect the Tweak Tool if it was from the software center, however if it was from a ppa then there could be dependency issues .

I installed a newer version of Gnome from this repo: 

[http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu)

---

### Post by mc4man on 2014-07-22
"Error: schema com.canonical.indicator.appmenu.hud not installed"
try installing the schema to see if it's installed, ect.
```
sudo apt-get install hud
```

---

### Post by bratromas on 2014-07-23
> **mc4man said:**
> try installing the schema to see if it's installed, ect.
```
sudo apt-get install hud
```

This worked great! The tweak tool is working again as it normally did. I don't know how I managed to remove hud from my computer, but I did and I had no idea. I'll mark this thread as solved immediately. :p

Thanks to both of you. I learned a lot from all of this.

---

