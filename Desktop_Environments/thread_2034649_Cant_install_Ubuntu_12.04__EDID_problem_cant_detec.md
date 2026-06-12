---
title: "Cant install Ubuntu 12.04  EDID problem cant detect monitors"
date: 2012-07-28
forum: Desktop Environments
---

### Post by Puttycat on 2012-07-28
[U][I][B]-Asus P5q pro
- Intell Q6600 2.4ghz quad core
-4Gb Ram 800 mhz
- Nvidia GTX 560 TI ( 2gb Edition )
- OCZ Agility 3 SSD 60gb ( Boot drive )
- 250gb STATA 2 HHD  ( Storage/music/files/etc..)
- 750 watt PSU[/B][/I][/U]

[B][I][U]- I-Inc 19" Monitor  ( Main )
- Dell 17" Monitor ( Icons , Widgets...etc. )[/U][/I][/B]

When i Try Booting from a Live CD Everything seems to be Loading okay until i get a error  saying something about not being able to find the EDID.  from what i can  tell it has something to do with Ubuntu / Video card not being able to  get the info from my monitors.

_***i have tried the following.***_
- use only one monitor at a time , then use the other one
- tried installing ubuntu on my SSD inside a laptop then put the SSD in my Desktop.
- tried using both DVI Connectors. 
**** I am using a DVI to VGA adapter. *****
- Ubuntu 11.10 worked just fine _***BUT***_ i was using a HIS ATI HD 4670  512mb VRam with the same setup. 
- i don't have any other monitors i can swap out and try. 

 please if anyone has any Advice on how to fix this problem??? 
i really Love/want to use Ubuntu but i dont understand why it isn't working now.

- im also going to try to download the daily build of Ubuntu 12.10 to see if that works.
     ( 7/29/2012 the 12.10 Live CD doesn't work either. (T.T)  ) 
[B][I][U]
Thanks In Advance. [/U][/I][/B]

---

### Post by banshee10000 on 2012-09-05
Hi there, This might be a bit late but her goes anyways

There is a few things you can try

in BIOS Under MAIN / Storage Configuration, change "Configure SATA as..." to [AHCI]. This allowed the kernel to find disks and boot.

For the EHCI issue while booting, under ADVANCED / USB Configuration, change "BIOS EHCI Hand-Off" to [Disabled].

For good luck, also made sure ACPI 2.0 is enabled under power saving.

Thats about all that I know that might solve some of it. But I have no idea on your EDID issue though
Best of luck to you

---

### Post by Bashing-om on 2012-09-05
Puttycat;

 Also IRT the EEID problems: papibe has info at this link:
[http://http://ubuntuforums.org/showthread.php?t=1946208](http://http://ubuntuforums.org/showthread.php?t=1946208)

Looked to be helpful, at least a good start toward resolution.

[INDENT]hth <==BDQ
[/INDENT]

---

### Post by papibe on 2012-09-05
me what? ):P

I think you refer to [this]("http://ubuntuforums.org/showthread.php?t=1857772&highlight=edid") and [this]("http://ubuntuforums.org/showthread.php?t=1946208").

Regards.

---

### Post by Puttycat on 2012-09-14
Thanks Guys, i figured it out...kinda... 32-bit didnt want to play nice with my desktop but for some reason the 64-bit version of ubuntu work just fine... strange, right?

---

