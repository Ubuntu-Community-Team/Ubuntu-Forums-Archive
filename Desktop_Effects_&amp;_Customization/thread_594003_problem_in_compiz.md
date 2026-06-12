---
title: "problem in compiz"
date: 2007-10-27
forum: Desktop Effects &amp; Customization
---

### Post by ][soSo][ on 2007-10-27
hi every one

i'm new on linux and this is my first try :)

i installed Ubuntu 7.10  and every thing looks good and i started like it.

but i have problem 

  i installed Cumpiz but when i click on CompizConfig Settings Manager it's not open!!
i don't know why!:confused:

i have ATI and installed xgl

and maybe this will help


```
S@Ubuntu:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


```

```
S@Ubuntu:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
S@Ubuntu:~$ 

```

==========

 


thank u all

---

### Post by ][soSo][ on 2007-10-27
this is my laptop [http://za.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=ZA&DISC_MODEL=0&highlightOption=94688&com.broadvision.session.new=Yes&PRODUCT_ID=114275](http://za.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=ZA&DISC_MODEL=0&highlightOption=94688&com.broadvision.session.new=Yes&PRODUCT_ID=114275)

---

### Post by Saint Angeles on 2007-10-27
if you use the new fglrx (8.42.3) you can use aiglx instead of xgl

---

### Post by ][soSo][ on 2007-10-27
area you sure this will fix the problem!

and how to get that thing?

---

### Post by ][soSo][ on 2007-10-28
any help plz :(

---

### Post by ][soSo][ on 2007-10-28
i still have compize problem 

i need help plz

---

### Post by ][soSo][ on 2007-10-28
comeon guys, i believe someone can help me

---

### Post by HokeyFry on 2007-10-28
aww man, i had this exact problem, hang on, lemme try to remember what i did to fix it.... just letting u know im here workin on it

---

### Post by ][soSo][ on 2007-10-28
ok thank u 
i'm waitng your reply :)

---

### Post by HokeyFry on 2007-10-28
umm what repo did u install compiz from?

if you dont know post your sources.list file

/etc/apt/sources.list

---

### Post by ][soSo][ on 2007-10-28
i don't remember !! it's from somewhere in this forum :D

do u want me to uninstall it again?

---

### Post by HokeyFry on 2007-10-28
no, just post your sources.list

the path is /etc/apt/sources.list

---

### Post by Forlong on 2007-10-28
Your problem might to related to this: [http://ubuntuforums.org/showthread.php?t=580063](http://ubuntuforums.org/showthread.php?t=580063)

---

### Post by ][soSo][ on 2007-10-28
this is the sources list

```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://sa.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://sa.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://sa.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://sa.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://sa.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://sa.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://sa.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://sa.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://download.tuxfamily.org/3v1deb feisty eyecandy 
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

---

### Post by ][soSo][ on 2007-10-28
> **Forlong said:**
> Your problem might to related to this: [http://ubuntuforums.org/showthread.php?t=580063](http://ubuntuforums.org/showthread.php?t=580063)

thank u,   i will try that :)

---

### Post by Forlong on 2007-10-28
> **'][soSo][ said:**
> this is the sources list
```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy 
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```
Yes, it's exactly the problem from the aforementioned sticky thread.

---

### Post by ][soSo][ on 2007-10-28
should i delete that ?

---

### Post by Forlong on 2007-10-28
Yes.
> you have to completely remove all compiz and libcompizconfig packages, make sure his repo [those two lines] is removed from your sources.list, then reinstall compiz.

---

### Post by ][soSo][ on 2007-10-28
thank you man :)

i will try this and tell you the result :)

---

### Post by ][soSo][ on 2007-10-28
thank you thank you thank you thank you thank you thank you :D:D
hurray!  it's working now :D

thank very much, i love you all :D

---

### Post by ][soSo][ on 2007-10-29
hello again

2 icons are missing and it's not on the list:confused:

3d Windows 

cube atlantis

look at the picture.

---

### Post by Forlong on 2007-10-29
Those are no official Compiz Fusion plugins and therefore not in Gutsy.
If you want to use them, you will have to wait until someone makes packages for them or compile 'em yourself.

---

### Post by ][soSo][ on 2007-10-29
is there a way to get that?

---

