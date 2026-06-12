---
title: "Fans turn on later"
date: 2007-10-20
forum: Dell  Ubuntu Support
---

### Post by anigwei on 2007-10-20
Hello,

I have had Ubuntu Feisty and now Gutsy in an Inspiron 1501 (AMD Turion 64 bit).

In Windows, when temperature raises 46-48º, the cooler turns on.

In Linux (either Feisty and Gutsy), the temperature raises to 55-57º, and then the cooler turns on... I think this is bad for the CPU....

I have seen some utilities for tweaking this, but not for 64 bit :(

It's a BIOS question? (I just recently updated to newer version)

Thank you

PD1: Throthling runs correctly (800Mhz major part of time).

---

### Post by dacap06 on 2007-10-28
The i8kutils package controls fn button operation and CPU fan speed for Dells in (K)Ubuntu.  I suspect that the table for i8kmon is merely set differently than the table Windows uses.  The good news is that you can change it to whatever you want the temperature thresholds to be.

You can find everything you need to make the changes in the /usr/share/doc/i8kutils/ directory, but here is an excerpt from the i8kutils README file to get you started:

THE I8KMON APPLET/DAEMON
========================

The i8kmon program can be used to monitor the CPU temperature and control
automatically the fans accordingly to user-defined temperature thresholds.
The program can be run as daemon or as an applet which can be embedded in
the Gnome panel. The program requires Tcl/Tk (>= 8.0).

The program has builtin defaults and temperature thresholds but users can
specify their own settings in configuration files /etc/i8kmon and ~/.i8kmon.
The daemon defines 4 states with different fan speeds ({0 0}, {1 0}, {1 1},
{2 2}) and for each state are defined the temperature thresholds which cause
the switching to a higher or lower state. Furthermore each state can have
different thresholds for operation on ac power or battery. 

For example the following configuration:

    set config(0) {{0 0}  -1  60  -1  65}
    set config(1) {{1 0}  50  70  55  75}
    set config(2) {{1 1}  60  80  65  85}
    set config(3) {{2 2}  70 128  75 128}

---

### Post by anigwei on 2007-10-29
hello Dacap06!

I've take a look, but I can't make work i8kutils under 64bit :(

The package is available only in i386, and I can't find the way of make work the source files.

In addition, the module i8k doesn't exist :(

Any help for 64 bit? 

Thx again

---

### Post by dacap06 on 2007-10-29
THe only modules arei8ktuils and i8kfan.  If they are not in the 64 bit repositories, I'm stuck.  You might want to double check that you have enabled the universe and multiverse repositories.

---

### Post by bluedragon436 on 2007-10-30
I don't have the 64bit, and still am having an issue with this...I keep my laptop on a cooling pad all the time when I am using it so it is not as big of an issue for me, but would still like to keep my computer running as cool as possible...

---

