---
title: "Gnome 3.10/Ubuntu 14.04 Theme &amp; Crashing Issues"
date: 2015-09-13
forum: Desktop Environments
---

### Post by ryanchang on 2015-09-13
Hi All,

Very distressing issue I have going here. First, I tried to upgrade my 14.04, but got the "not all upgrades can be applied..." message. Tried to remove the problem PPAs. Didn't help with the upgrades, so decided not to worry about it. Then, I removed a program called "schooltool" that runs on python in Synaptic, because I didn't need it. 

Restarted my computer and -- lots of problems!

First of all: icons, theme and shell environments are *not* loaded properly.

1) Have to log-in twice to enable the keyring; 

2) Starting up tweak-tool crashes. Sends me back to log-in screen;

I first tried to manually change the theme and icons through the terminal ... 

3) Now starting up the terminal also gives me the same issue. Gnome crashes, sends me back to log-in screen. 

Wish I could you give a debug output, but alas. 

I tried to attach a screenshot, but when the menu came up to upload the file, it immediately disappeared, and everything crashed and sent me back to the log-in screen. 

Help?

Ryan

---

### Post by Frogs Hair on 2015-09-14
I would start with the PPA purge if you haven't already tried. [http://askubuntu.com/questions/307/how-can-ppas-be-removed](http://askubuntu.com/questions/307/how-can-ppas-be-removed)

After at least 3 attempts with the Gnome PPAs Ive ended up reinstalling each time. My experience with those PPAs might be different than other users, but Ill be staying away from that one on daily user machines.

Edit: If this was an upgrade attempt to 14.10 that release has reached end of life and that may account for the package related problems.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by ryanchang on 2015-09-14
Hi Frogs Hair,

No, it wasn't an update to 14.10, just some packages that needed updating. There was an out-of-date PPA that needed to be removed, which I did, and then all the problems.

Do you have any suggestions of how to uninstall and reinstall GNOME if my terminal keeps crashing?

---

### Post by Frogs Hair on 2015-09-16
Remove and reinstall the gnome-shell  from the software center or synaptic package manager if installed. You can also check if xterminal is crashing which will allow you to enter the same commands the gnome terminal. ```
sudo apt-get install --reinstall gnome-shell 
```

---

### Post by ryanchang on 2015-09-16
Have tried reinstalling GNOME to no change. Chrome and XTERM working, but attempting to load GNOME's terminal/tweak tool has crash. 

I remember I tried something else before posting on this forum. Might it have something to do with gdk-pixbuf not loading properly? During my update process, I saw that this was not loading, so I tried to run the command recommended (something like: gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache), but it returns "No such file or directory." 

EDIT: Seems that components of GNOME environment -- icons, buttons, etc. -- are crashing upon loading. Again, I tried to screenshot an output from the terminal, but it keeps crashing and won't let me. Though I do see several lines that start with "GLI_OBJECT" running as errors in the terminal. 

Reinstalling/fixing this problem? Please advise!

---

### Post by Frogs Hair on 2015-09-17
Was it the linked PPA ? [https://launchpad.net/~schooltool-owners/+archive/ubuntu/ppa](https://launchpad.net/~schooltool-owners/+archive/ubuntu/ppa)

If so there are no 14.04 packages and can't guide you as what may be broken. Was this an upgrade from 13.10 ?

---

### Post by ryanchang on 2015-09-18
That ppa is not in my system, and this was a fresh install from a USB. 

Might this be an issue with the gdk-pixbuf I mentioned above?

---

### Post by Frogs Hair on 2015-09-19
> I tried to upgrade my 14.04, but got the "not all upgrades can be applied

Update or upgrade ?

 > I removed a program called "schooltool" that runs on python in Synaptic, because I didn't need it. 

I take it this was the repository version.

> Tried to remove the problem PPAs. Didn't help with the upgrades, so decided not to worry about it.


What PPA's ?

---

### Post by ryanchang on 2015-09-19
1) Update -- sorry.

2) I removed schooltool via Synaptic; and the other one via the Terminal.

3) This other PPA: It was giving me a 404 upon "apt-get update", so I got rid of it. And--perhaps I may have ****ed myself with this--I don't remember.

---

### Post by Frogs Hair on 2015-09-20
Try some clean-up for any un-needed packages. If you see any errors run suggested commands if applicable.  
```
sudo apt-get autoremove
``````
sudo apt-get clean
``` Remove Residuals:```
sudo apt-get remove --purge $(sudo dpkg -l | grep "^rc" | awk '{print $2}' | tr '\n' ' ')
``` Finally:```
 sudo apt-get update
``````
 sudo apt-get upgrade
```

---

### Post by ryanchang on 2015-09-20
Followed your instructions, but still no change.

---

### Post by Frogs Hair on 2015-09-21
Were you able to update without error and this a Gnome Shell installation or did you install the entire Gnome Desktop session. ?

---

### Post by ryanchang on 2015-09-21
This command: ```
sudo apt-get remove --purge $(sudo dpkg -l | grep "^rc" | awk '{print $2}' | tr '\n' ' ')
``` didn't produce any output.

And yes, this is an entire Gnome session (running Ubuntu Gnome Desktop).

---

### Post by Frogs Hair on 2015-09-22
If there were no residual packages then the command would not apply. See if there is output to the following command. ```
sudo apt-get install -f
```

---

### Post by ryanchang on 2015-09-23
"0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded"

---

### Post by Frogs Hair on 2015-09-23
It appears then that there are no-longer any package related problems. Try the following and then log out and back in if the command is found.  
```
sudo /usr/bin/gdk-pixbuf-query-loaders --update-cache
```

---

### Post by ryanchang on 2015-09-23
"Command not found." Have tried this before with the same result.

Also--and this has been happening since the problems started--have been unable to unlock keyring; none of my preferences load either (eg., I use a DVORAK layout, and I have to manually select it). 

Just crashed again, but this time slower, and noticed the error: "saned disabled edit /etc/default/saned"

---

### Post by Frogs Hair on 2015-09-23
I had doubts about the command , because the origin was the Arch forums. I located a bug page.  [https://launchpad.net/ubuntu/+source/gdk-pixbuf/+bugs](https://launchpad.net/ubuntu/+source/gdk-pixbuf/+bugs)

I haven't found a Ubuntu specific command. To query-loaders a package may need to be installed this is what I see when run the following.

```
$ gdk-pixbuf-query-loaders
The program 'gdk-pixbuf-query-loaders' is currently not installed. You can install it by typing:
sudo apt-get install libgdk-pixbuf2.0-dev

```

Source:[http://forum.siduction.org/index.php?topic=4915.0](http://forum.siduction.org/index.php?topic=4915.0)

---

### Post by ryanchang on 2015-09-24
Ran the command, am missing a bunch of a dependencies; said they would not be installed. I have filmed a [little video of the process]("https://www.youtube.com/watch?v=xc1X-w2SPWI"); seems that I am missing a glib package that belongs to GNOME3: [https://launchpad.net/~ricotz/+archive/ubuntu/red/+build/6694650](https://launchpad.net/~ricotz/+archive/ubuntu/red/+build/6694650) . 

However, as you can see at the end of the video, I have a crash. I tried to capture the full error message, but it's some failure to download a package. I'll try to get a better one later today.

---

### Post by Frogs Hair on 2015-10-02
The missing package appears to be from one the ricotz Gnome PPA's . Check software and updates > other software to see exactly what ppa sources are installed.  You can use the command also. 
```
grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by ryanchang on 2015-10-16
Hello,

Sorry for the late reply! In the time between replies, I have booted into recovery mode and run dpkg in an attempt to repair broken packages. I have many packages that need to be updated (see attached photo) in addition to the ricotz ppa, and also many PPAs that are no longer accessible for some reason. 

Would it suffice to remove the missing PPAs, as well as uninstall the programs associated with them? I am also wondering if there is an automated way to do this via the terminal, as my crashing issues have gotten worse. 

Additionally, would an upgrade to the current 15.04 help to solve this problem? I am a bit concerned about this avenue, as I have my machine dual-booted, and cannot risk bricking this computer into nothingness. 

Ryan[ATTACH=CONFIG]264989[/ATTACH][ATTACH=CONFIG]264990[/ATTACH][ATTACH=CONFIG]264991[/ATTACH]

---

### Post by Frogs Hair on 2015-10-17
I see that you are using the gnome PPA/s. If it is possible to login and back up your files do so. Reinstalling is a less painless and time consuming way deal with this problem. My luck with even the stable Gnome PPA  lead to re-installation on three different attempts before I gave up. ;)

---

### Post by ryanchang on 2015-10-18
That's the answer I wasn't hoping for! I can login, but I'm kicked out after GNOME crashes. I have a liveUSB that I can use to xfer to an external HDD.

Two-part question: Should I reinstall or update from LiveUSB? And will it affect my Windows 8 partition?

---

### Post by Frogs Hair on 2015-10-18
Re-installing would be the best option . I dual boot with Win 7 PRO HP (UEFI) and briefly with Win 10(Legacy Bios)  and all I've done is update GRUB. I have never used Win 8 or upgraded with a package system problems.

---

### Post by ryanchang on 2015-10-18
OK, great. Thanks. 

Is updating GRUB a potentially painless operation? And, I am curious if reinstalling with elementaryOS is a bad idea. Thoughts?

---

