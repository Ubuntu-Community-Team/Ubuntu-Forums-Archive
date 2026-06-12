---
title: "WoW Fails to Open?"
date: 2007-07-20
forum: Gaming &amp; Leisure
---

### Post by cupps on 2007-07-20
I am running Ubuntu 7.04, and have installed Wine 0.9.33, the default one packaged with the distro.

I installed both WoW and BC easily, copying them to my harddrive first. Whether or not I do the RegEdit tweaks, the "-opengl" tag or download the suggested DLLs (I now have them all), I get the same result:

WoW opens to the launcher, and then starts the opening movie perfectly, and it runs well. Then, whether I wait or skip the movie, it makes a click sound, like logging in, and then closes. No error, nothing, just closes. Here's the terminal view of what happens:

fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d470000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d470000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33ede4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f328,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f05c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f554,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f540,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:win:EnumDisplayDevicesW ((null),0,0x33f05c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB

I've been serching forums and guides for close to 12 hours. I'm ready to rip my hair out. Earlier, I tried messing with the video drivers (I have an ATI Radeon IGP 340M/440M/540M card), and everything I did made the problem worse until I started over.

Please, anyone... help. If I can get WoW into Wine, I no longer need Windows... and I'm getting desperate.

---

### Post by Syke on 2007-07-20
I can offer 2 suggestions:

1. Upgrade to the latest wine - instructions at [WineHQ]("http://www.winehq.org/site/download-deb"). This may or may not help.

2. Get an Nvidia card. WoW runs great on Nvidia. If at all possible, do this. ATI cards just don't cut it for Linux.

---

### Post by cupps on 2007-07-20
I just upgraded to 0.9.41 of wine, per your suggestion and no dice. Also, I'm on a laptop, so getting a new card is a big pain in the ***.

I ran WoW in Ubuntu back when the patch came out that caused the infamous targetting bug, and it worked fine then (save for the bug). Also, I used to run it in Windows with this same card and it worked, albeit not super well. Is there any way of getting WoW to play with my current setup?

---

### Post by cupps on 2007-07-20
If it matters... I can run glxgears at 350-375 FPS consistently. I was told on IRC that this likely means that the issue is with Wine and not my ATI card.

---

### Post by hikaricore on 2007-07-20
> **cupps said:**
> If it matters... I can run glxgears at 350-375 FPS consistently. I was told on IRC that this likely means that the issue is with Wine and not my ATI card.

I run glxgears at roughly 2800fps on a 2nd rate PCI (not PCIe) nvidia card.

350fps in glxgears is really really bad.  keeping in mind that it's not an actual benchmark tool, but as a guideline that's bad.

How did you install your ATI drivers and is your card supported properly by their latest driver?

---

### Post by cupps on 2007-07-20
I'm just using the default drivers from installing Ubuntu. I'm on a laptop, so changing graphics cards is out, and given that I used to run WoW on this machine, I"m not into buying a whole new box for WoW.

Earlier today I tried finding/installing better drivers for my ATI card, and had awful luck. So this time around, I've just left the defaults, since it's the closest I've gotten to running WoW.

Trying to get the flgrx (sp?) driver or others caused WoW to stop even earlier with the "unable to start 3d acceleration" message.

---

### Post by Nkari on 2007-07-20
How accurate is gears as a benchmark anyway?

Isn't the point of gears just to see if GL is at least sort of working?

---

### Post by Syke on 2007-07-20
What does it say when you type "glxinfo | grep direct" in a terminal?

---

### Post by cupps on 2007-07-21
It says Direct Rendering: Yes.

---

### Post by Canuckelhead on 2007-07-21
what about Cedega?  was't that supposed to run WoW no prob?  I'm not much of a gamer but transgaming has a good rep... but you need to pay 5 bucks a month 4 updates...

---

### Post by Nkari on 2007-07-21
It is supposed to be way better under wine

---

