---
title: "Desktop effects ATI readeon Xpress 1100 in feisty"
date: 2007-05-20
forum: Desktop Environments
---

### Post by Samputer on 2007-05-20
Hi

I have an acer aspire 5100 laptop - im presuming this is the UK version, as some i have seen have a webcam built in etc.

The major specs are as follows

120 gig PATA HDD
AMD turion 64 X2
ATI Radeon Xpress 1100
a gig of RAM

I have been using linux on and off for the past few years and i have decided to give feisty a go

installed it, everything went perfectly, i was very impressed with the wireless working out of the box, so i decided to stick with it and i am using it now.

I tried to enable the desktop effects by the simple settings in the preferences>desktop effects menu

i click enable and all that happens is that a dialog box appears with, desktop effects cannot be enabled, no explaination at all

I have installed the ATI drivers that ubuntu detected were required within the restricted driver manager and i have followed a few instructions from forums however i am quite a n00b and and i got errors which i didnt know what they meant.

so any help would be required - i think that the beryl and compiz effects are fantastic from various videos i have seen and it would be great to get them working

I am currently revising for some exams for tomorrow so thanks for any of your help but i might not be able to reply until late on tomorrow:(

Thanks in advance

Samputer

PS i think i have posted this in the right forum im not certain though... sorry if its wrong...

Edit: i meant radeon in the title - typo...

---

### Post by trigun on 2007-05-20
the desktop effects that come with feisty  are very buggy....try beryl instead;)

---

### Post by juanvicfer on 2007-05-21
First of all I would like to say hello! ( I'm new in this forum).

I think that i've got the same problem. I've been using Beryl in my girlfriend's Computer for a while, everything worked smooth....
Now, I have installed a fresh copy of feisty in my desktop computer and noticed that ATI drivers are not compatible with Desktop effects. I disabled the restricted drivers and managed to enable desktop effects, but it worked not very well ( there were unexpected shadows and some image problems).

I guess that it's because ATI drivers are not free. Anybody knows the answer????

Thanks in advance!

---

### Post by Samputer on 2007-05-22
First of all, hey juanvicfer, im pretty new here too lol and yeah thats the exact problem im having apart from when i disable the restricted drivers and enable beryl - its very painful lol - nothing works right any slight animation etc completely just goes fuzzy lol. Glad to know im not alone lol

Hey Trigun, ive tried to install beryl and nothing happens, unless i have disabled the drivers so i am assuming that the drivers are the main problem i really would like to get these to work so if anyone knows of any way to do this, I would really appreciate it.

Thanks

Samputer

---

### Post by Samputer on 2007-05-22
i have just  tried to run beryl within terminal and got the following feedback if it could help anybody

> :~$ compiz
/usr/bin/compiz.real: No composite extension
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension


thanks

Sam

---

### Post by Samputer on 2007-05-22
I just tried to uninstall the restricted drivers and run it all again and since then it has said "composite manager not available" rather than the usual desktop effects cannot be enabled once its opened.i had this problem before when ubuntu was first installed and i fixed it somehow but i cant remember how...

Samputer

---

