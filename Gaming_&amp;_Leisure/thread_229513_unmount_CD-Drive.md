---
title: "unmount CD-Drive"
date: 2006-08-04
forum: Gaming &amp; Leisure
---

### Post by Derek Djons on 2006-08-04
After spending almost 20 minutes reading and searchin on Google I gave up and decided to ask for help here.

I've installed WINE and use it to install and play some 2D games I have such as all the Blitzkrieg strategy games and Commandos I, II & III.

When I start installing the game, after minutes it asks for the second CD / DVD. Since my portable only has one drive I'm forced to unmount the drive in order to swap CD's. Well, here comes the problem. Of course pressing the drive button doesn't works. Right-clicking on the drive icon on my desktop also doesn't works. It gives an error that the unit is busy. Opening a terminal and unmounting it using 'umount' and additional options also doesn't works.

On the internet I only found certain vague CLI commands (which all failed trying it)... does anybody know how to force it to unmount WITHOUT fooling the config files. Because I've tried that also and it doesn't recognized the 2nd CD as second, but as the first.

---

### Post by DoktorSeven on 2006-08-04
Open a terminal, mount the drive, make sure you have nothing else open (like nautilus) that has the contents of the CD displayed, then specify the full path to the setup file from anywhere besides inside /media/cdrom/ (or wherever your CD is mounted):

```
wine /media/cdrom/setup.exe
```

You should be able to unmount and mount a second CD then, since you aren't inside the CD directory, which causes the "busy" messages.

---

### Post by Derek Djons on 2006-08-05
Unfortunately this option also did not work. Some games consisting out of two disc can be copied to one folder on the hard drive without important files being overwritten. I think I am going to try that.

---

### Post by ZylGadis on 2006-08-05
This is an unfortunate bug in Windows that some older game installers seem to fall into. In Windows you don't need to unmount a drive before mounting it again, which means that some game installers do not take the effort to do the thing right, and don't unmount the first install cd before asking you to insert the second one. I have the same problem with Baldur's Gate original installer.
Naturally, linux insists you do the thing right and unmount one cd before mounting the next one. Which means that while the installer (in wine) is tying up the cd drive, you can't do much about it. If you force it to unmount (with umount -l, afair), the installer crashes, as you effectively cut its link to the cd drive. If you kill the installer in order to unmount the usual way, naturally it can't continue.
The usual solution is to copy all cds of the game to your hard drive, mount them as separate cds, and use winecfg to cheat the game installer that the cd images are actual cd drives. It won't work with all windows game installers, though. If that does not work and there is no loki (or other) installer for the game, unfortunately you can't do much besides cursing the stupidity and incompetence of various windows-related people.
Something else you could try, if you have access to windows, is install the game there and copy the game directory to linux.

---

