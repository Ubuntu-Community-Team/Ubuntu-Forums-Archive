---
title: "X Server Issues"
date: 2007-03-19
forum: Desktop Environments
---

### Post by andrewlondonuk on 2007-03-19
Hi, i was wondering if somebody from here could help. I've just brought a widescreen laptop with an intel i950 integrated graphics card. All was going well until i tried to get it to support 1200x800. Anyway, i installed the 915 resolution hack, then i checked what resolutions it had set up with 915resolution -l, it listed 1200x800 so i restarted the X server. This is when the problems started. I couldn't get x windows to start so i checked my x.org.conf file and there was no mention of 1200x800. I added it to the .conf file but when i tried to run start x i was given the following error:

Fatal Server Error:
NO SCREENS FOUND
X10: fatal IO error 104 (connection reset by peer) on X Server ":0" after 0 requests ( 0 known processed) with 0 events remaining.

This is quite worrying because i'm on a PHP course at the moment and really need to get the laptop going for use in the evenings.

The monitor section of the xorg.conf file says the following:

Section "Monitor" 
Identifier "Generic Monitor"
Option "DPMS"
Horiz Sync 28-51
Vert Sync 43-60
End Section

Is there anyone out there that can help me get this sorted because i'm in major mess without access to this laptop, i removed Vista to install ubuntu so help me stick with it and get this working. Please. :D


Thanks in advance.
Andrew

---

### Post by denver on 2007-03-19
try the following command

> dpkg-reconfigure xserver-xorg

to go through the configuration steps manualy. It will ask you questions about your hardware and resolution preferances.

OR
> dpkg-reconfigure -phigh xserver-xorg

to let dpkg guess the correct setup for your hardware.

you could also try finding details about your monitor online ( Horiz Sync and Vert Sync ) and manualy add them to the conf file if the above fail.

---

### Post by andrewlondonuk on 2007-03-19
I've done that and manuall added the vert and horzinal sync  details and it's still spitting out the following:

Fatal Server Error:
NO SCREENS FOUND
X10: fatal IO error 104 (connection reset by peer) on X Server ":0" after 0 requests ( 0 known processed) with 0 events remaining.

Is there anway to remove the 915 resolution tool because when i installed that it said there was a conflict but installed it anyway.

It might be that doing it?

---

### Post by zvacet on 2007-03-19
reported conflict,but you installed anyway?Why?It is good chance that uninstall will correct your problem.

---

### Post by denver on 2007-03-20
to uninstal a package you just type:

> apt-get remove <package name>

or

> apt-get --purge remove <package name>

to purge the configuration files for that package. If you are unsure about the name of the package...just type

> dpkg -l | grep 915

and all the packages with 915 in the name will be listed. You could check the Xserver error log in /var/log to find out more about the problem.

Good Luck!

---

