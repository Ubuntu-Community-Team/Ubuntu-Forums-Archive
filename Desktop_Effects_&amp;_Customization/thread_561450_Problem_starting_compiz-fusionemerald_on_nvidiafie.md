---
title: "Problem starting compiz-fusion/emerald on nvidia/fiesty"
date: 2007-09-27
forum: Desktop Effects &amp; Customization
---

### Post by cudds on 2007-09-27
Hey guys - I'm trying to get compiz-fusion up and running on my Vostro 1700.

I have a Nvidia card and got all the driver from their site installed fine.

When I try to start compiz-fusion I get this error;

```
dan@dan-ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0407 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald

(emerald:7597): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7597): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7597): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7597): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7597): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7597): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7597): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7597): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7597): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7597): Wnck-WARNING **: Unhandled action type (nil)
Segmentation fault (core dumped)
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
```

I've checked that I have all the upto date libwnck8 libwnck-common libwnck-dev. 

It appears to be a problem with emerald but I can't tell what - running emerald --replace doesn't start either and just gives the same errors.

---

### Post by Dark Hornet on 2007-09-27
Are you running the "desktop effects" that come with Fiesty, or did you download Compiz Fusion?

---

### Post by drchaos619 on 2007-09-29
same problem!

please help!!!

---

### Post by unebaguettesvp on 2007-09-29
same exact problem!!!!
someone help us!

---

### Post by UberPsyX on 2007-10-01
and me :(

---

