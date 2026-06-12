---
title: "Firefox slow, fades in &amp; out in Gnome (Kubuntu 9.04)"
date: 2009-05-06
forum: General Help
---

### Post by chellrose on 2009-05-06
I just upgraded to Jaunty from Hardy last week.  I like it so far.  It's pretty :)

However, I notice that in Firefox (3.0.10, in Gnome), things seem to slow down randomly.  For instance, I can be scrolling down on a page, or trying to highlight text (ordinarily not an issue) and FF suddenly freezes for a few moments and the process becomes really slow.

When this happens, or when I open a new tab that takes longer than normal to load (lots of big images, for example), the screen goes grayscale and I can't do anything with it for a while.  It eventually goes back to normal -- sometimes after a few seconds, sometimes it takes 5 minutes.

Not sure if this is a bug or a PICNIC... but can anyone offer a suggestion? :confused:

Thanks!

---

### Post by modmadmike on 2009-05-06
> **Sissy13 said:**
> I just upgraded to Jaunty from Hardy last week.  I like it so far.  It's pretty :)

However, I notice that in Firefox (3.0.10, in Gnome), things seem to slow down randomly.  For instance, I can be scrolling down on a page, or trying to highlight text (ordinarily not an issue) and FF suddenly freezes for a few moments and the process becomes really slow.

When this happens, or when I open a new tab that takes longer than normal to load (lots of big images, for example), the screen goes grayscale and I can't do anything with it for a while.  It eventually goes back to normal -- sometimes after a few seconds, sometimes it takes 5 minutes.

Not sure if this is a bug or a PICNIC... but can anyone offer a suggestion? :confused:

Thanks!

install the restricted drivers for your Graphics card.

---

### Post by modmadmike on 2009-05-06
> **modmadmike said:**
> install the restricted drivers for your Graphics card.

oh and if its an Intel card then i can't help you there, I have had this problem on my Eee PC

---

### Post by chellrose on 2009-05-06
> **modmadmike said:**
> install the restricted drivers for your Graphics card.

OK... how do I go about finding those?  Can you give me the newbie version? :?

Thanks!

---

### Post by modmadmike on 2009-05-06
> **Sissy13 said:**
> OK... how do I go about finding those?  Can you give me the newbie version? :?

Thanks!

System>Administration>Hardware Drivers then install the one with the largest number

---

### Post by chellrose on 2009-05-06
> **modmadmike said:**
> System>Administration>Hardware Drivers then install the one with the largest number

Only driver listed is something for my Atheros wireless card.  But, right now I'm using wired ethernet.

It took about a day to get my wireless working again after the upgrade, so I'd rather not mess with that again if possible! :)

---

### Post by -kg- on 2009-05-06
This issue happens to me at times, and I have a very well supported wireless chipset.

I think what happens is that, when processing and waiting, some of the programs will seem to freeze, and the screen will dim.  I don't know what causes this, but I also have these issues from time to time.

Do a few searches in Synaptic and see if the same thing happens.  Occasionally, I'll put in a search term and, if the search takes particularly long, the same thing will happen with Synaptic.

This laptop is a < 1 year old Toshiba and has very good specs, so I'm relatively sure it isn't a specs problem, especially since with Jaunty everything that I have tried has worked right out of the box (even off the Live CD).

I have a dim memory of seeing a setting somewhere that will cause this action in a long search or operation, but I can't for the life of me remember where I might have seen this, nor am I confident that I actually saw it.  But that is what I surmise is going on.  As for the pausing occasionally when paging down an already downloaded page, perhaps the "nice" settings are too low for Firefox?

---

### Post by colau on 2009-05-07
> **Sissy13 said:**
> I just upgraded to Jaunty from Hardy last week.  I like it so far.  It's pretty :)

However, I notice that in Firefox (3.0.10, in Gnome), things seem to slow down randomly.  For instance, I can be scrolling down on a page, or trying to highlight text (ordinarily not an issue) and FF suddenly freezes for a few moments and the process becomes really slow.

When this happens, or when I open a new tab that takes longer than normal to load (lots of big images, for example), the screen goes grayscale and I can't do anything with it for a while.  It eventually goes back to normal -- sometimes after a few seconds, sometimes it takes 5 minutes.

Not sure if this is a bug or a PICNIC... but can anyone offer a suggestion? :confused:

Thanks!

From terminal can you
```

lspci
cat /proc/swaps

```

---

### Post by chellrose on 2009-05-07
> **-kg- said:**
> 
Do a few searches in Synaptic and see if the same thing happens.  Occasionally, I'll put in a search term and, if the search takes particularly long, the same thing will happen with Synaptic.


It doesn't happen to me with Synaptic; oddly enough the searches seem to be really fast, even for things which normally bring up a bunch of packages, such as "tex".  However, I haven't really gotten used to Synaptic's way of doing things yet -- having used Adept for so long. :D

I have a Toshiba laptop as well, but mine is 4 years old.

---

### Post by chellrose on 2009-05-07
> **colau said:**
> From terminal can you
```

lspci
cat /proc/swaps

```

lspci:
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)

```

cat /proc/swaps:
```
Filename                Type        Size    Used    Priority
/dev/sda5                               partition    650592    2740    -1

```

:confused:

---

### Post by animamia on 2009-05-08
I have the same problem with Firefox 3.0.10 on Ubuntu Hardy 8.04. Some websites I often surf started slow down from 3.0.9. Can't open many pages coz Firefox freezes and I have to restart Firefox.

Anyone else has the same problem? And is there any fix for it?

---

### Post by colau on 2009-05-08
No problem with firefox 3.0.10 in ubuntu 9.04 so far.

---

### Post by jahLux on 2009-05-08
> **animamia said:**
> I have the same problem with Firefox 3.0.10 on Ubuntu Hardy 8.04. Some websites I often surf started slow down from 3.0.9. Can't open many pages coz Firefox freezes and I have to restart Firefox.

Anyone else has the same problem? And is there any fix for it?

Forget Firefox - It's been slow on Ubuntu since 3.0.6 - download and install Shiretoko from the Mozilla stable. Its 'light-years' ahead of the 'Fox'

---

### Post by HyroShamy on 2009-05-12
I had this problem (Firefox and Opera both freezing and going greyscale randomly) along with several others (drag and drop took forever, and occasionally Opera would crash and consume around 93% of the CPU resources). I seem to have solved all problems by disabling Avant Window Navigator. I don't know why this program would cause these problems; my best guess is that the Autohide and Keep Below Maximized Windows features might have had something to do with it.

---

### Post by chellrose on 2009-05-12
> **HyroShamy said:**
> I had this problem (Firefox and Opera both freezing and going greyscale randomly) along with several others (drag and drop took forever, and occasionally Opera would crash and consume around 93% of the CPU resources). I seem to have solved all problems by disabling Avant Window Navigator. I don't know why this program would cause these problems; my best guess is that the Autohide and Keep Below Maximized Windows features might have had something to do with it.

Thanks; and forgive my ignorance, but how do I disable Avant?  I can't find it in any of the menus.  I *do *have a file /usr/share/app-install/desktop/avant-window-navigator.desktop, but I can't find anything in it that looks like an enable/disable.  Here's what it contains:

```

[Desktop Entry]
X-AppInstall-Package=avant-window-navigator
X-AppInstall-Popcon=2871
X-AppInstall-Section=universe

Type=Application
Name=Avant Window Navigator
Comment=A dock-like window navigator.
Exec=avant-window-navigator
Icon=avant-window-navigator
Categories=GNOME;Utility;

X-Ubuntu-Gettext-Domain=app-install-data

```

---

### Post by HyroShamy on 2009-05-13
Avant is a program that is similar to the Dock on a Mac. If it is running you should know, The circled area below is the Avant Window Manager while it is running. I doubt you have it running; the file you found was not the program itself but a reference to it.
[IMG]http://i658.photobucket.com/albums/uu304/hyroshamy/avant.png[/IMG]

Just in case you do have it running, you can disable Avant by: 1)right clicking on the bottom of it and selecting close and 2)go to System -> Preferences -> Sessions and if Avant is listed under Additional Startup Programs, deselect it. 
If you don't have Avant running, I'd try disabling Compiz (System-> Preferences -> Appearance, select the Visual Effects tab, and then select none) and seeing if the problem persists.

---

### Post by chellrose on 2009-05-14
Thanks.  I disabled the Visual Effects, and it seems to be working, at least for now.

---

### Post by gnomungus on 2009-06-10
I've been having this problem too, though I use a Lenovo T400 and I'm using regular old Ubuntu 9.04. I'm pretty sure that it has something to do with the Radeon video card. I had a lot of problems getting the proprietary drivers installed in the first place, and disabling visual effects stops the weird fading behaviour. Oh well. hopefully Radeon will get their Linux driver act together one of these days ...

---

