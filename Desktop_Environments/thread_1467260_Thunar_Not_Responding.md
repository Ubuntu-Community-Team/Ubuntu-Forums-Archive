---
title: "Thunar Not Responding"
date: 2010-04-30
forum: Desktop Environments
---

### Post by mlhudson on 2010-04-30
So, suddenly I can't get Thunar to respond beyond ONE LEVEL of clicking with my mouse. I click on one directory, and then no files or directories in that next level may be opened/selected/anything. It just gets stuck. 

I'm thinking I must have bumped some control, but I can't for the life of me figure out what's up.

I reinstalled using Synaptic hoping it would fix the issue. I rebooted several times. No joy.

Any help to debug this issue?

---

### Post by halilonat on 2010-05-01
i do have same problem, after i updated my karmic koala to lucid lynx, thunar started not to respond any activity, and when i right click on the files, it responds like there is an empty space. double click and using keyboard to enter is useless!

---

### Post by Jose Catre-Vandis on 2010-05-01
It's a bug in GTK in Lucid

Workaround is to use any view other than Detailed, so choose Icon or Compact. You can go to Detailed by pressing CTRL + 2, Icon CTRL + 1, Compact CTRL + 3 on keyboard.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Can also offer a fix of sorts (although you lose some of the button and window smoothing in general)

You need a running copy of Xubuntu Karmic and have to copy two files:

/usr/lib/libgtk-x11-2.0.so.0
/usr/lib/libgtk-x11-2.0.so.0.1800.3

On Xubuntu Lucid rename/backup the corresponding files:

/usr/lib/libgtk-x11-2.0.so.0
/usr/lib/libgtk-x11-2.0.so.0.2000.1

The first file will probably disappear as it is a shortcut to the second file, but do not worry.

Then as sudo/root, copy the two Karmic files into /usr/lib

Log out/login in and Detailed view should work OK, but you will notice some changes to the interface (a bit squarer/clunky instead or more rounded and smooth)

You should easily be able to reverse this change by replacing the original files

NB: This is not as clever as I first thought, and seems to break other parts of the system, e.g. could not open up Hardware Drivers from the system menu, unless I reverted.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This bug has been known about for months, and is crazy it has not been fixed in time for the LTS release

---

### Post by doixanh on 2010-05-01
Confirmed error. Work around by selecting by mouse and getting in the directories with Enter (do NOT double click!)

A bit weird but it works for me :D

---

### Post by miegiel on 2010-05-02
The bug report : [https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/520118](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/520118)

---

