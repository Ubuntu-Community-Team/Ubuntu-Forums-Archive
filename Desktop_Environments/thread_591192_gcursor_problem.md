---
title: "gcursor problem"
date: 2007-10-25
forum: Desktop Environments
---

### Post by tdb1001 on 2007-10-25
Since upgrading to ubuntu 7.10 gcursor runs but selecting a cursor theme fails to change anything. If ran from a terminal I see the following 4 libglade warnings:

(gcursor:7678): libglade-WARNING **: could not find signal handler 'extract_theme'.
(gcursor:7678): libglade-WARNING **: could not find signal handler 'open_theme_dir'.
(gcursor:7678): libglade-WARNING **: could not find signal handler 'entry_selected'.
(gcursor:7678): libglade-WARNING **: could not find signal handler 'size_changed'.

Any help would be much appreciated!

---

### Post by eZtaR on 2007-10-26
I am having the exact same problem

---

### Post by duncan.hawthorne on 2007-10-26
same here
you should post it as a bug at launchpad

---

### Post by balcis on 2007-10-27
yeah plus 1, same problem. i installed by the synaptic of course (and also first bean for ubuntu :) )

---

### Post by Xgen on 2007-10-27
Yes, gcursor doesn't work in 7.10, but cursors can be changed through Preferences--->Appearance--->Customize--->Pointer...or through gconf.

---

### Post by digby280 on 2007-10-28
> **Xgen said:**
> Yes, gcursor doesn't work in 7.10, but cursors can be changed through Preferences--->Appearance--->Customize--->Pointer...or through gconf.

Thanks Xgen.  I knew there must be a simple answer to that problem.

---

### Post by vitalejd on 2007-10-30
Is there any way to get a customized cursor?  I have one downloaded but how do I get it work work now that gcursor doesn't work in 7.10 righ tnow?

---

### Post by tdb1001 on 2007-10-31
Thanks Xgen, that solves the problem for me.

---

### Post by Redenbacher on 2007-11-15
To install your own custom pointer, extract the .tar into your .icons folder "/home/USERNAME/.icons" and it will then show up in Appearance -> Theme -> Customize -> Pointers 

Select your theme and wait a couple of seconds, and you should see it!

---

### Post by kholburn on 2007-12-09
> **Xgen said:**
> Yes, gcursor doesn't work in 7.10, but cursors can be changed through Preferences--->Appearance--->Customize--->Pointer...or through gconf.

I tried that and it worked ...  partly.  Now I have my new cursors when the mouse is over a window but the default when it is over a title bar or the desktop.

(Installed kubuntu and added gnome and compiz and am now running gnome and compiz).  

I also notice that the window title bars and surrounds are controlled by compiz but there doesn'tseem to be any way of changing the cursor for them.  I had a poke around in System->Preferences->Emerald Theme Manager but no place to change cursors.

---

