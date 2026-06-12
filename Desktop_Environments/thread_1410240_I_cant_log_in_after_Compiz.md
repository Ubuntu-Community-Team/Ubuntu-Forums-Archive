---
title: "I cant log in after Compiz"
date: 2010-02-18
forum: Desktop Environments
---

### Post by seanbw on 2010-02-18
I configured compiz and afterwards the pc froze. The offendiing option was the minimize effect. Once I clicked the water effect after choosing the minimize option, the whole system froze and I had to reinstall Ubuntu.
After reinstalling ubuntu, I again configured compiz and after choosing all my options avoiding minimize and water, I could not log in afterwards. I just get a blank screen.
These are the scripts I ran without success:
```

compiz --replace gconf
glxinfo
killall compiz.real
ccsm
compiz --replace gconf
sudo killall -9 gdm
sudo killall ccsm
metacity --replace
sudo killall compiz.real

```
Ater running metacity --replace, I got borders round the terminal and nothing else. Just a blank screen
I am now in Ubuntu Live CD and trying to resolve this without reinstalling.
I then stumbled to this thread [HTML]http://ubuntuforums.org/showthread.php?t=799070&highlight=login+problems+compiz&page=72[/HTML] and have have run the Compiz check and I got the following:
```
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2a02 detected.

Would you like to know more? (Y/n) y

 Your particular graphics chip may be blacklisted on certain distributions.
 However that does not necessarily mean you will not be able to run Compiz.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards.

Do you want to skip blacklist checks by Compiz? (y/N) y

```I then ran compiz and got the following:
```
ubuntu@ubuntu:~$ compiz
Checking for Xgl: not present.
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log
Detected PCI ID for VGA:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present.
Checking for nVidia: not present.
Checking for FBConfig: present.
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present.
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
```I don't want to reinstall ubuntu. What can I do to clear compiz and go back to a default installation status.

Please can any one help?
Regards
Sean

---

### Post by seanbw on 2010-02-18
Bump! Anybody? Have tried the solution on this thread:
[http://ubuntuforums.org/showpost.php?p=8407028&postcount=9](http://ubuntuforums.org/showpost.php?p=8407028&postcount=9) 
but still no joy.
Thx to anyone that can help!

---

### Post by seanbw on 2010-02-18
This seems to have been the cause of the problem.
[https://help.ubuntu.com/community/CompositeManager/CompizFusionIntel](https://help.ubuntu.com/community/CompositeManager/CompizFusionIntel)

In case it affects other people. Problem was caused by intel card gma X3100 (GMA965) and the workaround is given in the link.

Hope it helps someone else.
Cheers

---

