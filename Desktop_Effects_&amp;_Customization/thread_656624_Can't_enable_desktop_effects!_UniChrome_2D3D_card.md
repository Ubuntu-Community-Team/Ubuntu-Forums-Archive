---
title: "Can't enable desktop effects! UniChrome 2D/3D card"
date: 2008-01-02
forum: Desktop Effects &amp; Customization
---

### Post by mfk on 2008-01-02
I know many people have this problem, but I could not find the answer in any of the other threads. I have a UniChrome 2D/3D integrated video chip. It is a VIA KM 400/8237 motherboard. I know when I did have windows on the same machine I did have NAVIDA and/or RAID drivers installed. Should I install them now that I'm running Ubuntu? Is there any hope for these "desktop effects" to be enabled on my comp? Thanks in advance.

---

### Post by overdrank on 2008-01-02
> **mfk said:**
> I know many people have this problem, but I could not find the answer in any of the other threads. I have a UniChrome 2D/3D integrated video chip. It is a VIA KM 400/8237 motherboard. I know when I did have windows on the same machine I did have NAVIDA and/or RAID drivers installed. Should I install them now that I'm running Ubuntu? Is there any hope for these "desktop effects" to be enabled on my comp? Thanks in advance.

HI and maybe this will help
[https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome)
Good luck!

---

### Post by mfk on 2008-01-02
Thanks for helping me once again. I really don't understand any on the source code that I've been reading...I'm trying to learn it. So.....I found this page that somewhat tells me what I'm supposed to do, but I'm still lost....please help me with this. I don't know a better way of pasting their text so here it is. Also I noticed that it's from October 2005.  Here is what they said:
 
Re: new via unichrome driver
Quote:
Originally Posted by xombie
...
For the 640x480 problem have you tried manual settings for your monitor. If automatic monitor detection fails x will default to a "don't kill the monitor mode".
There actually was a bug reported on this at x.org. This is why I think that Ubuntu Dapper is using an older via driver.

Quote:
Bug#318348: xserver-xorg: Unichrome driver will only use 640x480 on KM400

Tom Huckstep
Thu, 14 Jul 2005 16:53:52 -0700


Package: xserver-xorg
Version: 6.8.2.dfsg.1-2
Severity: normal
Tags: patch


There's a bug in the Unichrome driver code which means high resolution video
modes are not available. There's a simple fix given to me by Luc Verhagen
of the Unichrome development team:

In the file programs/Xserver/hw/xfree86/drivers/via/ (provided by
patches/000_stolen_from_unichrome.sf.net.diff), in the function
ViaGetMemoryBandwidth:

case VIA_KM400:
if (pVia->ChipRev < 0x8F)

should read:

case VIA_KM400:
if (pVia->ChipRev < 0x84)


Making this change and recompiling has solved the problem for me.

Cheers,

Tom

---

