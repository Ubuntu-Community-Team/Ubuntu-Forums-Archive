---
title: "NO Desktop after reboot? knit: no resume image..."
date: 2008-03-03
forum: Desktop Environments
---

### Post by seeker1458 on 2008-03-03
I just got done installing syslog-ng and went to do a reboot.  I get the grub loader, and the ubuntu splash screen, but the system loads to the shell, not the desktop environment.  I have tried running "sudo apt-get install ubuntu-desktop" and it says that I've got the most current version.  So I tried re-installing it, no luck.  I also tried reconfiguring xserver.  But when I finish and type "startx" it flicks to a black and white checker-boarded screen with a big black "X" as the pointer, then shuts the monitor off.  Tower still is up and running but no signal is being put out to the monitor.  I can log in through shell and access files and such, but why is my nice desktop now a black screen?  

Upon boot this is what I get:

Starting up...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/1164e1-2530-4687-9aad-f8cba13417ab = s
da5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/1164e1-2530-4687-9aad-f8cba1341
7ab
kinit: No resume image, doing normal boot...

Ubuntu 7.10 syslog1-desktop tty1

syslog1-desktop login:

***don't be confused, the name of the system is syslog1...not going to be used for anything but a syslog server***

---

### Post by fracturedmorals on 2008-03-03
try this:
```
sudo /etc/init.d/gdm restart
```

or this:
```
sudo tail -f /var/log/Xorg.0.log
```


The resume image thing is just ubuntu looking for an image of the system in case you tried to do a hibernate. :)

It sounds like you may be having driver issues, and these are usually good ways to get some slightly more verbose output for diagnostic purposes.

Please post your results.

---

### Post by seeker1458 on 2008-03-03
Ok i tried the gdm restart. This is what I got:

*Stopping GNOME Display Manager...     [OK]
*Starting GNOME Display Manger...        [fail]

I dont get it everything was fine befor the reboot.  The system had been built for two days, now syslog-ng makes the gdm screwy?

How do I go about fixing that?

---

### Post by pbcartwright on 2008-03-03
do you have an NVIDIA or ATI card??
what driver do you have for video in /etc/X11/xorg.conf ?
if it says nvidia, change it to nv then:

/etc/init.d/gdm restart

---

### Post by seeker1458 on 2008-03-03
when I try to run /etc/X11/xorg.conf.

I get :
-bash: /etc/X11/xorg.conf: Permission denied

I can't sudo into it it says command not found.

---

### Post by seeker1458 on 2008-03-03
The box is an IBM Think Centre 8432, I think its intel video

---

### Post by seeker1458 on 2008-03-03
duh, vi /etc/...

Ok:
Section "Device"
              Identifier     "Intel Corporation 82865G Integrated Graphics Controller
Driver     "intel"
BusID     "PCI:0:2:0"
Option   "UseFBDev"         "true"

---

### Post by fracturedmorals on 2008-03-03
> **seeker1458 said:**
> when I try to run /etc/X11/xorg.conf.

I get :
-bash: /etc/X11/xorg.conf: Permission denied

I can't sudo into it it says command not found.

try changing "intel" to "vesa" for the time being.

Also....you might be able to find the specific problem if you select the option to look at the log when gdm gives you that error.

---

### Post by pbcartwright on 2008-03-03
you don't run xorg.conf, it is the configuration file for the X-windows system.
type:
more /etc/X11/xorg.conf

and page through it. You will see the keyboard settings, mouse settings, monitor settings and video settings.
mine looks like this:
  Driver         "nvidia"

to reconfigure your video try typing this line:

dpkg-reconfigure xserver-xorg 

and it will walk you  through the config

---

### Post by seeker1458 on 2008-03-03
ok went through the xserver config. And ran "startx" 

Got:
everything fine until...
(WW) VESA(0) Failed to set up write-combining range(0xf000000, 0x7d00000)
(EE) AIGLX: Screen 0 is not DRI capable

Waiting for X server to shut down FreeFontPath: FPE "/usur/share/fonts/X11/misc"
refcount is 2, shoudl be 1; fixing.

xauth: error in locking authority file /home/syslog1/.Xauthority

---

### Post by pbcartwright on 2008-03-03
were you root when you did that?? "#" prompt? or you must run sudo COMMAND

try looking at that file again:
more /etc/X11/xorg.conf and see if there is a line with "dri".. you may need to edit that file and comment out that line. Sounds like you picked something wrong in the dpkg-reconfigure

my MODULE section has these ( every setup is different)
Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"

no DRI..

---

### Post by pbcartwright on 2008-03-03
another thing you can try. When you reboot, do you have the option of picking an older kernel version?? if it installed a newer kernel, you might be able to use the older one, OR try the failsafe..

---

### Post by seeker1458 on 2008-03-03
I don't see a module section?

---

### Post by seeker1458 on 2008-03-03
i tried un-installing gdm, and got an error.  Give me a second and I'll type it back up.

---

### Post by seeker1458 on 2008-03-03
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:3201: parser error : Extra content at the end of the document
gtk-update-icon-cache: symbol lookup error: gtk-update-icon-cache: undefined symbol: g_option_context_new
Errors were encountered while processing:
  Fas-user-switch-applet
E: Sub-process /usr/bin/dkpg returned an error code (1)

---

### Post by pbcartwright on 2008-03-03
did you try rebooting and either selecting an older kernel or failsafe?

---

### Post by seeker1458 on 2008-03-03
Hit esc when loading and have three options

Regular 7.10
7.10 recovery

neither of these allows me to get to my desktop.

I am just making a nother install, copying the files I need, and then rebuild again using one partition.  I just don't get why something got changed in the first place.

---

### Post by pbcartwright on 2008-03-03
it is always good to make TWO partitions, "/" root and /home for your personal stuff. that way, when you have to reload, or want a different OS, your personal stuff, application settings, EMAIL, bookmarks, are saved..

---

### Post by seeker1458 on 2008-03-03
quick question, on when I installed the new copy of 7.10 I told it to bring over the user information from the previous install.  Everything went fine but there is a syslog-ng folder in the new install.  Did pulling the user data over also bring all the dependant libs? ie, Glib, GETTEXT, etc...?  Or do I need to reload all that manually? Do you know a way to check and see if I am actually using syslog-ng instead of syslogd?

---

### Post by fracturedmorals on 2008-03-03
Do you already have an xserver running?

try ctrl + alt + f7(f8 f9....)
to see if you already have an xserver running......if not, try (Yet again)

```
sudo /etc/init.d/gdm restart
```

(I'm thinking even though GDM didn't properly start before it might still have a lock)

---

