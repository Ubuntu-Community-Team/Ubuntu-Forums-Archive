---
title: "gnome missing, cant log in"
date: 2014-03-23
forum: Desktop Environments
---

### Post by mikee2 on 2014-03-23
As a total novice I recently removed Nautilus, and gnome and everything that came with it, and was unable to log back into computer. So now I am trying to fix it without re-intsalling all of ubuntu (i have all kinds off stuff i want to keep).

Is there a way to install gnome and nautilus or a way to access the terminal before log in?

Any help is appreciated!

---

### Post by deadflowr on 2014-03-23
Try 
```
ctrl + alt + F1
```
at the login screen.
Which should bring up a console.
Login like normal and trying reinstalling gnome.
```
sudo apt-get install gnome
```

might work, might not.

Anyway,
Ubuntu is a gnome desktop with unity as its user interface.

Why did you think otherwise?

---

### Post by mikee2 on 2014-03-23
thanks that was helpful.  I chose not to use nautilus in the beginning because it seriously lacks navigation controls, such as UP a level, and tabbed browsing. Kinda silly a major OS comes with such a flimsy FM system. That being said, I chose to revert because of problems with Truecrpyt. When i uninstalled Nautilus, it uninstalled EVERYTHING, including gnome. SO i got it all back installed now, and use PCmanFM  as my FM

---

### Post by deadflowr on 2014-03-23
Nautilus simply lacks an arrow to move up a level, but is still simple and easy to do.
The name of the folder currently in will be listed right above the main window.
As well as the next window up, and so on.
Simply click on it will move you to which ever level up you click.

As well, it does have tab browsing.

What it lacks is split pane view.
Among other things, I forget.

---

### Post by grahammechanical on 2014-03-24
At the boot menu we have an option to select Recovery Mode. Now, it all depends upon the version of Ubuntu that you have installed. You neglect to tell us. If you cannot see any reference to recovery mode then look for Advanced Options for Ubuntu. It is a sub-menu and in that menu you will see Recovery Mode.

At the Recovery Menu select Network. That will make a network connection which you will need if you are going to install software. Running Network will also put the file system into Read/Write mode which is necessary if we are going install software or edit system configuration files.

Then run Root. That will put you at the command line where you can run commands to install software. When you are finished type exit and you will go back to the Recovery menu where you can select Resume and you may get to a desktop.

You should know this: Nautilus is more than a simple file manager. It is deeply integrated into the desktop environment. Removing Nautilus breaks the desktop. Also Gnome is the desktop environment for Ubuntu. Removing Gnome breaks Ubuntu.

If we do not like Gnome or the standard Ubuntu user interface then it is better to install one of the Ubuntu flavours that meet our requirements.

Regards.

---

