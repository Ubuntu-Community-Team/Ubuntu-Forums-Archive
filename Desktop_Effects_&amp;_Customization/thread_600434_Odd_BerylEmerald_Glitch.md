---
title: "Odd Beryl/Emerald Glitch"
date: 2007-11-02
forum: Desktop Effects &amp; Customization
---

### Post by seismicmike on 2007-11-02
I'm getting an odd glitches with Beryl/Compiz/Emerald.

When I have Metacity as the window manager and GTK as the Window Decorator (default settings in Ubuntu), then everything is normal, like so:

[IMG]http://img206.imageshack.us/img206/5812/screenshotaj8.png[/IMG]

But when I make Beryl the window manager and Emerald the decorator, then my windows have no borders or title bars, like so:

[IMG]http://img111.imageshack.us/img111/4552/screenshot1bc1.png[/IMG]

When I have Compiz as the manager I can't move my windows around.

Does anyone know what might be causing this? Thanks.

---

### Post by Forlong on 2007-11-02
What version of Ubuntu are you using and what type of graphics card / driver?

---

### Post by jogorman on 2007-11-02
Make sure you have Compiz installed. Try opening a terminal and running it by hand and when there is no window border and see is any errors are reported.

---

### Post by seismicmike on 2007-11-02
Compiz is definitely installed. In fact I just got an update of it throught he update manager and it still has the same problems.

I'd really like to have Beryl and Emerald playing nice.

As far as your questions, Forlong. I'm running Ubuntu 7.10... at least I think.... I upgraded to the beta of Gutsy about 2 weeks before the release of the official Ubuntu 7.10, and I never actually did a dist upgrade to go to the full version. I'm assuming that was unnecessary though b/c I just kept ketting updates and such.

At any rate, I have no idea about the graphics card stuff... It's whatever was built into my laptop... Gateway m320s if that helps... here's my lspci:

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
02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

Thanks guys

---

### Post by Forlong on 2007-11-03
First of all: remove Beryl.

Then post the output of ```
compiz
``` in a terminal.

---

### Post by maestrobwh1 on 2007-11-03
From a similar experience when I had Feisty Kubuntu (KDE), I can tell you that getting rid of beryl and upgrading to compiz-fusion will help, and google "Trevinos repositories" and add the eye-candy repos to your sources.list before doing so.  They are more "experimental" but just seemed to give me fewer issues and more effects plugins.

I also have Gutsy on my machine and the version of compiz-fusion in the Gutsy repo seems great so far. I find Gutsy to be WONDERFUL compared to other ubuntu/kubuntu versions.

I like to keep two versions of Kubuntu on my machine, as I have the drive space and it seems to be a fail safe option:-)

---

### Post by seismicmike on 2007-11-03
> **Forlong said:**
> First of all: remove Beryl.

Then post the output of ```
compiz
``` in a terminal.

OK... I did that. Compiz does work now while allowing me to move windows around.

Here's the Terminal output:

```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:3582 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
```

---

### Post by seismicmike on 2007-11-03
> **maestrobwh1 said:**
> From a similar experience when I had Feisty Kubuntu (KDE), I can tell you that getting rid of beryl and upgrading to compiz-fusion will help, and google "Trevinos repositories" and add the eye-candy repos to your sources.list before doing so.  They are more "experimental" but just seemed to give me fewer issues and more effects plugins.

I also have Gutsy on my machine and the version of compiz-fusion in the Gutsy repo seems great so far. I find Gutsy to be WONDERFUL compared to other ubuntu/kubuntu versions.

I like to keep two versions of Kubuntu on my machine, as I have the drive space and it seems to be a fail safe option:-)

Can you tell me what those repos are?

---

### Post by Forlong on 2007-11-04
> **seismicmike said:**
> OK... I did that. Compiz does work now while allowing me to move windows around.
Great. But still no window boarders?
Install ccsm ```
sudo apt-get install compizconfig-settings-manager
``` and make sure the Window Decoration plugin is enabled.

If it is, go here and see if this can help you out: [http://wiki.compiz-fusion.org/Intel_with_AiGLX](http://wiki.compiz-fusion.org/Intel_with_AiGLX)

---

### Post by seismicmike on 2007-11-08
The big question is can I get a cube?

---

### Post by Forlong on 2007-11-09
See [here](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) under "Getting the cube".

---

