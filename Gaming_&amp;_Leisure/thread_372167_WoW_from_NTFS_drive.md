---
title: "WoW from NTFS drive"
date: 2007-02-27
forum: Gaming &amp; Leisure
---

### Post by Tangee on 2007-02-27
Hi,

I have just set up my laptop to dual boot, but so far have only allocated 8GB for ubuntu (at the minute, prior to testing), but would still like to try WoW on it.

I have installed wine as per the HOWTO's, and am now wondering if it is possible for me to run WoW directly from my windows install as I don't have the space to install it on the ubuntu drive. I have been away from linux for a while now and I'm not sure how the NTFS writing is going, or whether there is a way to have a separate config file or WTF folder on the linux drive and pass this to the wow executable?

---

### Post by Sammi on 2007-02-28
Great news for you: NTFS write support just became stable on feb. 21. with the release of version 1.0 of the NTFS-3G driver!!! See here for very good instructions on making it work in Ubuntu: [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

After making ntfs writing work, you should be able to run the wow.exe file in you WoW folder with Wine, with a simple command like this one: ```
wine wow.exe -opengl
```
You should also look through the Ubuntu WoW/Wine community howto: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by Tangee on 2007-02-28
this is good news! one problem down then!

I installed ntfs-3g and it works fine as far as writing to my windoze partitions goes.

I even got WoW started...kinda...

when I run it the console spews out some stuff, one of which is:

```
*********************************WARN_ONCE*********************************
File r300_render.c function r300Fallback line 406
Software fallback:ctx->Multisample.Enabled
***************************************************************************

```

and then the login screen appears, except the background image is scaled way up, to the point where i can see only a fraction of it, and I get 0fps! If I move the mouse the only way I see that the laptop is still taking input is if I alt-tab out and in again, whereby it moves to where it should be but is frozen again!

Any ideas?

---

### Post by Tangee on 2007-02-28
Sorry...that wasnt the messsage I was concerned about...

here is the total terminal output when I try to run it:

```
$ wine /media/hda2/Games/World\ of\ Warcraft/WoW.exe -opengl
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33edd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f33c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f544,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:win:EnumDisplayDevicesW ((null),0,0x33f04c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
*********************************WARN_ONCE*********************************
File r300_render.c function r300Fallback line 406
Software fallback:ctx->Multisample.Enabled
***************************************************************************
Try R300_SPAN_DISABLE_LOCKING env var if this hangs.

```

its that last line I'm wondering about...

---

### Post by Sammi on 2007-02-28
Seems like a graphics card driver related problem. Make sure you are not running Xgl, Compiz or Beryl. They don't work well with 3d applications, as they are all still unfinished and in development.

Make sure you have updated your drivers. Try reinstalling them as the installation might be borked. Anyway what graphics card are you using? Just so you know, ATI is a pain in the ****.

---

### Post by Tangee on 2007-02-28
I have Beryl installed but change to Metacity before trying WoW. 

lspci lists GFX card as ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] even though its a 9700 (problem?)

I am pretty sure I am using the latest open source drivers (how can I be sure, as I said i've been away from linux for ages!) but if I borked the install this is the only sign so far... :(

---

### Post by Sammi on 2007-02-28
Aha. I'm a Nvidia user myself, but I've heard that the open source ATI drivers aren't good for 3d or games. Try the proprietary driver: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Tangee on 2007-03-01
proprietary ones meaning the 'fglrx' driver?

from what I read Beryl won't work with those ones, and while Beryl isn't exactly integral to my usage it is mighty purty!

---

### Post by Sammi on 2007-03-02
> **Tangee said:**
> proprietary ones meaning the 'fglrx' driver?
Jup. 'ati' is the open source one.
> **Tangee said:**
> from what I read Beryl won't work with those ones, and while Beryl isn't exactly integral to my usage it is mighty purty!
I have no idea. Your call.

---

### Post by Tangee on 2007-03-02
woot! logging in fine, playing grand, except the laggy mouse...any advice on this one?

installed proprietary drivers using automatix2bleeder...seems to have remedied whatever I messed up!

PS. sorry to drag this one out but this is the last step to transferring my windows everyday computing to ubuntu!

---

