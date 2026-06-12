---
title: "Trouble loading i8kutils"
date: 2007-09-29
forum: Desktop Effects &amp; Customization
---

### Post by skyemoor on 2007-09-29
Because of erratic mouse problems on my Dell Latitude desktop (especially when warm), I've loaded i8kutils in order to set a lower temperature for fan turn-on, to see if that would solve the problem.  

Fiesty 7.04
Dell Latitude 810C
Pentium III 1133MHz
Both a synaptics touchpad and a TPPS/2 IBM Trackpoint

I loaded i8kutils from [http://packages.ubuntu.com/feisty/utils/i8kutils](http://packages.ubuntu.com/feisty/utils/i8kutils) , making sure I had all of the required dependent packages.  No problems during the load.

An applet was supposed to appear on the Gnome desktop control panel, but as yet has not.  In examining the terse documentation, it refers to /proc/i8k, which doesn't exist after the load, and doesn't show up in the list of files in the download package listed above.  

The documentation says to execute the following;

   $ cat /proc/i8k

But I get back;

   bash: $: command not found

All of the files in the download loaded without problem and are in their proper location.

Not surprisingly, the applet doesn't load into the Gnome control panel.

What have I done wrong?  How can I fix it?

---

