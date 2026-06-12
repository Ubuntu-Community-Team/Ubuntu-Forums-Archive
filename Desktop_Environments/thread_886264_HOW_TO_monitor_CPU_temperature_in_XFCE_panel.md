---
title: "HOW TO: monitor CPU temperature in XFCE panel"
date: 2008-08-11
forum: Desktop Environments
---

### Post by acy76 on 2008-08-11
I recently added a system monitor to the XFCE panel and found that there wasn't much information available that was specific to Xubuntu. I decided to use the Gnome panel sensor plugin instead of the XFCE version, as it's supposed to look a bit nicer.

The steps required are below:

1) Using synaptic or the terminal, install 'xfce4-xfapplet-plugin' (which allows Gnome panel applets to run on the XFCE panel).

2) Install 'sensors-applet' (which is the Gnome monitoring applet)

3) Install 'lm-sensors' (which is the actual sensor monitoring software)

3.1) Open a terminal window and execute the following command: 'sudo sensors-detect'.

This will guide you through the process of detecting sensors and adding kernel modules to monitor them. I answered YES to all the questions and allowed the script to automatically add the modules at startup. Alternately, these can be added manually.

4) Reboot (or manually start the kernel modules just identified by the sensors-detect script).

5) Once back on the desktop, right-click the panel and select 'add new item', and add 'XfApplet'.

5.1) XfApplet (the Gnome applet software) will present any Gnome panel applets it detects. Select 'Hardware Sensors Monitor'.

6) Monitor is now on the panel. Right-click and select 'preferences' to customize as desired.

And that's all there is to it.

---

### Post by woaibbhemm on 2008-08-12
hello~
    nice   to  meet  you   and     thank  you   for   youe   sharing ,  welcome   to   our   website  !












Welcome to usfine for [buy lotro gold](http://www.usfine.com/Lord-of-the-Rings-Online-US-c-93.html)Age Of Conan gold[/url] and 
[buy runescape gold](http://www.usfine.com/runescape-c-68.html)sevise.

---

### Post by abdusamed on 2009-10-11
is there ANY software for xubuntu which is like babylon's right click feature --> LOVE IT..cuz stardict only gives me random Chinese!

---

### Post by nsznaj on 2010-10-12
Great, all worked just fine.

Now, i'm getting these values, can someone say if they are normal of something is about to explode?

CPU 54 - 57 C, temp1 54 C, Core 0 44 C, core 1 47 C.
Here room temperature is around 20 C.

Cheers!

---

### Post by kosach on 2011-08-26
nsznaj,

Those values look perfectly fine... nothing has even reached 60 degrees,
and in my opinion the point where you should begin to worry would be probably around 65+.

---

