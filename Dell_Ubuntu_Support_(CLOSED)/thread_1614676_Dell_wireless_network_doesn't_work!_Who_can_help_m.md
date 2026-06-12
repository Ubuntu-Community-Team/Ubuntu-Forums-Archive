---
title: "Dell wireless network doesn't work! Who can help me? , have spent much much time"
date: 2010-11-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by PengMeng on 2010-11-05
My laptop is Dell Inspiron 1110 with Win 7.
I have Wubi installed Ubuntu 10.04, 64bit.
But the wireless card is not working, the wireless card is &#65314;&#65315;&#65325;&#65300;&#65299;&#65297;&#65298;&#65294;

[FONT=Arial][COLOR=black]My computer has no wire connection, also no CD driver. [/COLOR][/FONT]

[FONT=Arial][COLOR=black]How can solve the problem? Any one can help?[/COLOR][/FONT]

[FONT=Arial]P.S. [/FONT]
[FONT=Arial]I have used "lshw" command to show the hardware information.[/FONT]
[FONT=Arial]There are **three** "*network" information[/FONT] and one of them is "**disabled**".
My computer just has one wire network card and one wireless network card, I don't know why there are three network information. 

Any suggention will be appreciated!

---

### Post by ugm6hr on 2010-11-06
If you have no wired connection, it will be a nuisance to install the wifi drivers.
I have done this before, but am not 100% certain that a Wubi installed Ubuntu will behave the same way.
If you want to try:
[http://ubuntuforums.org/showpost.php?p=9263039&postcount=2](http://ubuntuforums.org/showpost.php?p=9263039&postcount=2)
Although you need the 64-bit version: [http://packages.ubuntu.com/lucid/amd64/bcmwl-kernel-source/download](http://packages.ubuntu.com/lucid/amd64/bcmwl-kernel-source/download) (not the i386 version)

---

### Post by P4man on 2010-11-06
This is essentially the same, but perhaps a bit easier:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access)

Dont see why it wouldnt work with wubi.

---

### Post by HannuMR on 2010-11-07
You must install Ubuntu by USB memory stick, because Wubi installed Ubuntu will crash down at the first updates.
After regular installation wireless network is possible.
Wubi is nice idea, but practical only for first trying, like live-Ubuntu.

---

