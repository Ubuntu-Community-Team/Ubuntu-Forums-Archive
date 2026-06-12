---
title: "Can't install Ubuntu on my Dell Latitude E6420"
date: 2011-08-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by qrwe on 2011-08-26
Hi there,

I have a Dell Latitude E6420, on which I would really like to install Ubuntu. However, as I boot up the Live image, the screen image suddenly hangs and I'm unable to do anything. I can hear from Ubuntu start sound that things are still ticking in the background, but I can't manage anything. The graphics card should be compatible, as it's either an Intel or Nvidia card. Moreover, even [ubuntu.com]("http://www.ubuntu.com") ranks this model as "certified" for Ubuntu use ([click here]("http://www.ubuntu.com/certification/hardware/201011-6842:201011-6843:201101-6947")).

Has anyone seen this problem before on this Dell model? If so, were you able to solve it somehow?

I had no problems with Ubuntu at my previous Dell Latitude D630, so one might wonder what's wrong. Thanks for any advice; cheers!

---

### Post by frogotronic on 2011-08-26
Hello,

  DELL images & drivers for the e6420 are on the DELL website.

  [CLICK HERE]("http://support.dell.com/support/downloads/driverslist.aspx?os=WN104&catid=-1&dateid=-1&impid=-1&osl=EN&typeid=-1&formatid=-1&servicetag=&SystemID=LAT_E6420&hidos=W764&hidlang=en&TabIndex=&scanSupported=False&scanConsent=False")

Install in order.

BIOS
IMAGE
Chipset drivers
Sound drivers
Card reader drivers
Video Drivers

  I've attached a copy of my XORG.CONF file.

- CH       :guitar:


- CH

---

### Post by qrwe on 2011-08-27
> **cement_head said:**
> Hello,

  DELL images & drivers for the e6420 are on the DELL website.

  [CLICK HERE]("http://support.dell.com/support/downloads/driverslist.aspx?os=WN104&catid=-1&dateid=-1&impid=-1&osl=EN&typeid=-1&formatid=-1&servicetag=&SystemID=LAT_E6420&hidos=W764&hidlang=en&TabIndex=&scanSupported=False&scanConsent=False")

Install in order.

BIOS
IMAGE
Chipset drivers
Sound drivers
Card reader drivers
Video Drivers

  I've attached a copy of my XORG.CONF file.

- CH       :guitar:


- CH

Thanks.

Supposing that you by "IMAGE" mean "Ubuntu Install CD", it still doesn't work after updating the BIOS. The screen is still half blank, half "striped" when booting with the Live CD. :-(

What also is interesting is that when I've waited some time for Ubuntu to boot up (which it didn't), I rebooted to my current Windows 7 installation. When it starts, the screen flickers as if it was "exhausted" from the last boot. The funny thing is: when closing the lit (to turn of the screen) for a while, the flicker is gone after a while :-S

Did I misunderstood about the "IMAGE"? Or am doing it wrong with the Live CD? Thanks again, and in advance!

---

### Post by frogotronic on 2011-08-28
> **qrwe said:**
> Thanks.

Supposing that you by "IMAGE" mean "Ubuntu Install CD", it still doesn't work after updating the BIOS. The screen is still half blank, half "striped" when booting with the Live CD. :-(

What also is interesting is that when I've waited some time for Ubuntu to boot up (which it didn't), I rebooted to my current Windows 7 installation. When it starts, the screen flickers as if it was "exhausted" from the last boot. The funny thing is: when closing the lit (to turn of the screen) for a while, the flicker is gone after a while :-S

Did I misunderstood about the "IMAGE"? Or am doing it wrong with the Live CD? Thanks again, and in advance!

Hi,

  Yes, IMAGE means a disc image, or ISO, or LiveCD, or Install CD.

  I'll assume that you've tried following this guide (or something like it) for dual boot: [http://www.hackourlife.com/dual-boot-windows-7-and-ubuntu-10-10-maverick-meerkat/](http://www.hackourlife.com/dual-boot-windows-7-and-ubuntu-10-10-maverick-meerkat/)

  _BEFORE you start with Ubuntu 10.10_:

    1) After you've burned the disc (image) to a CD, run the CHECK DISC FOR DEFECTS.

    2) Make sure that in your BIOS settings, **_the "Optimus" setting is checked for OFF_**.  Optimus is a software enabled real-time switching between Intel graphics and nVIDIA graphics - the switch only really works well for M$ based O/Ses.  If you're interested in getting this to "work" try the BumblebeeProject.
 
  _AFTER you've checked this_:

  Try booting the LiveCD. If you are still getting flickering screen,  post back.

  BTW: You CANNOT use 10.04 LTS with this machine, you must use 10.10.  This is because of the SandyBridge chip architecture. 

  Have a look at this post: [http://ubuntuforums.org/showpost.php?p=10803983&postcount=1](http://ubuntuforums.org/showpost.php?p=10803983&postcount=1)

- CH

---

### Post by tibike on 2011-11-27
The same happens with 11.10 on my E6420. 
I don't have the Optimus option in BIOS - I guess only have the Intel HD 3000 graphics (!? it's my work PC so I'm unsure. I could not find NVidia on my Win device manager !?). 

The USB live boot fails with a half black - half black and white vertical striped screen. 

Same happens for 32 bit, 64 bit and a RH-based Distro. 

Also tried to create the live USB drive with both UNetbootin and the Ubuntu Startup Disk creator. 

Any suggestions?

---

### Post by frogotronic on 2011-11-27
> **tibike said:**
> The same happens with 11.10 on my E6420. 
I don't have the Optimus option in BIOS - I guess only have the Intel HD 3000 graphics (!? it's my work PC so I'm unsure. I could not find NVidia on my Win device manager !?). 

The USB live boot fails with a half black - half black and white vertical striped screen. 

Same happens for 32 bit, 64 bit and a RH-based Distro. 

Also tried to create the live USB drive with both UNetbootin and the Ubuntu Startup Disk creator. 

Any suggestions?

If you need to shut-off the Optimus option, you ***must*** have bought the nVIDIA option.  If not, you don't need to worry about it at all.

However, you should download the Maverick Meerkat CD image from DELL, not the Generic 11.10 iso.  Then you can upgrade to 11.10.

**To shut-off the Optimus option**:

Press F12 repeatedly on BOOT

Then follow the images

You should be using A06 BIOS

---

### Post by tibike on 2011-11-27
Thanks Cement Head!
I didn't get the 10.10 iso part. 
Maverick it is then...

---

### Post by frogotronic on 2011-11-28
> **tibike said:**
> Thanks Cement Head!
I didn't get the 10.10 iso part. 
Maverick it is then...

Also, remember to install the drivers in order (Post #2), also available from the Dell Support site.

I'm running maverick with full updates and XORG SWAT and no problems at all.

- CH

---

### Post by Stoney_Fish on 2012-05-24
Dell Latitude E6420 Intel Sandybridge graphics (no nvida) installs ok on Ubuntu 12.04, but I get the black and white screen lockup in many games.

The display issue happens on some games when starting, some when exiting or some when changing the game display settings

Examples

"Open Arena" fails to start
"superTuxKart" when changing display settings.

The dell site provides drivers for Ubuntu 10.10 but not for 12.04

---

### Post by frogotronic on 2012-05-24
> **Stoney_Fish said:**
> Dell Latitude E6420 Intel Sandybridge graphics (no nvida) installs ok on Ubuntu 12.04, but I get the black and white screen lockup in many games.

The display issue happens on some games when starting, some when exiting or some when changing the game display settings

Examples

"Open Arena" fails to start
"superTuxKart" when changing display settings.

The dell site provides drivers for Ubuntu 10.10 but not for 12.04

If I were you, I'd add the Xorg edgers PPA to your sources and update & upgrade.

This will give the lastest Intel HD 3000 drivers.

Instructions are here: [https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=precise](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=precise)

MAKE SURE YOU READ THE INSTRUCTIONS.  INSTALL PPA-PURGE SO THAT YOU CAN REVERSE THE INSTALL IF IT GOES SOUTH.

- ch

---

