---
title: "can't enable most of compiz fusion effect"
date: 2007-11-22
forum: Desktop Effects &amp; Customization
---

### Post by adrianmak on 2007-11-22
I installed ubuntu 7.10 on my dell inspirson 1420.
Visual effect is enabled and I switch to "Extra" option

I tried some of the effects like Effects->Animations, Desktop -> Expo, Desktop->Desktop Wall, Extras->Window Preview, etc. I enabled them then go back to the CCSM main page, all previous checked effects will be uncheck. And sometimes window title bar will be disappear (i.e can't move window), I ve the got back to Normal and enabled visual effect again.

Whats wrong ? display card , display driver problem ?

my notebook is using integrated display card GMA X3100.

---

### Post by mrmiserable on 2007-11-23
under ccsm preferences plugin list make sure you have the automatic plugin list ticked

good luck

---

### Post by adrianmak on 2007-11-23
> **mrmiserable said:**
> under ccsm preferences plugin list make sure you have the automatic plugin list ticked

good luck


It is ticked.!!

---

### Post by lomion on 2007-11-23
Have you tried emerald as the windwo decorator to solve the border problem?

---

### Post by mrmiserable on 2007-11-23
ccsm preferences on the left panel

also what is output in terminal when you type compiz

---

### Post by adrianmak on 2007-11-23
> **lomion said:**
> Have you tried emerald as the windwo decorator to solve the border problem?


I have it installed and configured!!.


> **mrmiserable said:**
> ccsm preferences on the left panel

also what is output in terminal when you type compiz


This is the output:
grace@grace-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 0c) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format




Does my problem related to the hardware the integrated card GMAX3100 I'm using

Ive to put an option in xorg.conf to skip checking in order to enable visual effect.

---

### Post by mrmiserable on 2007-11-23
i have seen lots of threads with your graphics card and problems
also you can put gtk-window-decorator under ccsm window decoration this will give you metacity not emerald but it worth a try put it in command section


gtk-window-decorator --replace 

sorry

also it could be one of the plugins that is the problem open ccsm and turn of all plugins first 
process of elimination sort of

---

### Post by starcannon on 2007-11-23
I returned our Dell 1420n because of the X3100 graphics card, intel does a lot of things right, but video cards is not one of them. I did get compiz working with it, I don't remember now what I did, I do remember that if you enable then disable it, it wont enable again, think I just deleted the local settings in my home directory and let compiz build a new one for me and that got it going again.

Good luck, and even with that, the 1420n is still a great machine, it's just not big on 3d acceleration, its a great little work horse though.

---

### Post by adrianmak on 2007-11-23
> **starcannon said:**
> I returned our Dell 1420n because of the X3100 graphics card, intel does a lot of things right, but video cards is not one of them. I did get compiz working with it, I don't remember now what I did, I do remember that if you enable then disable it, it wont enable again, think I just deleted the local settings in my home directory and let compiz build a new one for me and that got it going again.

Good luck, and even with that, the 1420n is still a great machine, it's just not big on 3d acceleration, its a great little work horse though.

which directory should I delete to let compiz rebuild again ?

---

### Post by n6k6t6 on 2008-02-24
I have inspiron 1420n with nvidia graphics card, with factory-installed Ubuntu 7.10, and all 
Compiz effect run fine.  Good luck!

---

