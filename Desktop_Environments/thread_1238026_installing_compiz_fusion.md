---
title: "installing compiz fusion"
date: 2009-08-12
forum: Desktop Environments
---

### Post by dhaider on 2009-08-12
Hello,
I just made the switch to kubuntu and am a total newbie. I am slowly learning, but was getting very frustrated last night when i was trying to install compiz fusion on kubuntu 9.04. I looked at a couple of tutorials and it seemed that all i would have to do is go into kpackagekit and search compiz settings or something along those lines. But, my search  turned up anything at all. I am not sure what i am doing wrong. I searched open office, that did not turn up anything eihter. I know i can do this by the command line, but i want to to know what i am doing wrong with kpackagekit. Can someone let me know how to use the package manager to install compiz fusion. Sorry, if these are dumb questions, but i really need your help.

Thanks,
Danish

---

### Post by arky on 2009-08-12
From commandline you search for packages. 

$ apt-cache search compiz


$ apt-cache search openoffice.org 

Or you can use synaptic to search and install new packages

---

### Post by Tclarkie on 2009-08-12
yeah, search compiz in synaptic

---

### Post by dhaider on 2009-08-12
i can't find synaptic on my installation, i only have Kpackagekit...and nothing comes up when i search for that

---

### Post by charlesopondo on 2009-08-12
Try these steps:

1. Press the key combination Alt+F2 to invoke the 'Run' dialogue
2. In the dialogue type 'konsole' (without the quotes) then press 'Enter'. This should start the console.
3. In konsole at the command prompt type 'sudo apt-get install compiz' (again without the quotes) then press 'Enter'. You'll be prompted to type your password. As you type nothing will appear on the screen. When done press 'Enter'
4. You should then see something similar to this:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-plasma python-dev python2.6-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper compizconfig-backend-gconf libdecoration0
Suggested packages:
  nvidia-glx gnome-themes
The following NEW packages will be installed
  compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper compizconfig-backend-gconf libdecoration0
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 4806kB of archives.
After this operation, 25.8MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

5. Press 'y' to answer in the affirmative then wait for the process to complete.
6. To start compiz, type 'compiz &' (without quotes) at the command prompt.

I think, though, that you do not need compiz to enjoy the special desktop effects it provides if you're using KDE 4. If you have updated to the latest packages, just go to System Settings > Desktop to configure your desktop. I am enjoying these effects without compiz:

[IMG]http://www.facebook.com/photo.php?pid=2974452&l=ab71c355d5&id=633242703[/IMG]
Rotating cube displaying, among other things, Win XP in a virtual machine

[IMG]http://www.facebook.com/photo.php?pid=2974453&l=8f41ac21cb&id=633242703[/IMG]

---

