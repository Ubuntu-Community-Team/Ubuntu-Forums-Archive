---
title: "ASUS 22 inch monitor with Gnome"
date: 2007-06-30
forum: Desktop Environments
---

### Post by rzj on 2007-06-30
I have switched to an ASUS MW221 widescreen monitor. I changed the screen resolution selection to 1680x1050. The monitor is actually being driven at that resolution and the exact same vertical and horizontal frequencies as windows is using, however the Gnome desktop is still filling a 4:3 aspect ration section of the screen.

I tried updating the display section of xorg.conf to match all the display modes, copying entries someone else posted for this monitor, but nothing has changed.

I looked in gde.conf but I don't see anything that tells Gnome how big a desktop to draw.

SInce the mouse stops at the artificial boundary i presume it is X that is deciding I'm still in 1400x1050 or similar. I'm sure the display is correctly driven as the display is sharp whereas setting it to 1400x1050 gives a full width stretched but blurry picture.

Where do I set this?

It seems that for all Ubuntu's progress with hardware recognition at install time, it has no easy way to reproduce this mastery for hardware changes - unless I've missed something like a "rescan hardware" option.

Ray

---

### Post by deepclutch on 2007-07-01
this i feel is not a GNOME problem,but with Xorg.you can try widescreen configuring on Xorg with below hw2's.
Here the link is:
[http://gentoo-wiki.com/HOWTO_Widescreen_Resolutions_(WSXGA)]("http://gentoo-wiki.com/HOWTO_Widescreen_Resolutions_%28WSXGA%29")

---

### Post by coffeecat on 2007-07-01
> **deepclutch said:**
> this i feel is not a GNOME problem,but with Xorg.you can try widescreen configuring on Xorg with below hw2's.
[http://gentoo-wiki.com/HOWTO_Widescreen_Resolutions_(WSXGA]("http://gentoo-wiki.com/HOWTO_Widescreen_Resolutions_%28WSXGA"))

What a pity that's an empty wiki page.

**rjz**, I have absolutely no problem with 1680x1050 resolution and Feisty. You might help yourself by posting your xorg.conf so that others can see if there is an error in it or if the graphics driver is capable of driving the 1680x1050 resolution. For example if, by chance, you're using the vesa driver that won't give you more than 1280x1024 if I remember correctly.

Also post details of your graphics card. Again, some will not give you more than 1280x1024.  Certain older Intel chipsets with the i810 driver have this limitation.

---

### Post by rzj on 2007-07-01
I am fairly sure that the driver is working OK for the display mode. The monitor status says it is running at 1680x1050 65Khz and 60Hz.

This is exactly the same drive information that Windows XP is running it at (and displaying correctly). The screen appearance suggests also that it is correctly driven as the Gnome desktop is displayed full screen height but with black bands to left and right, and an aspect ratio that looks like a bit wider than 4:3 so that nothing looks distorted.

It is as if the hardware is being driven at 1680x1050 but that Gnome or X is limiting the graphical output to a width of maybe 1400. 

I've just tried setting the screen resolution to 1400x1050 and interestingly the hardware drive signal is unchanged - the monitor is stil being driven at 1680x1050, but the desktop is lower resolution and stretched to fill the display, yet all the lower resolutions I tried like 1280x1024 etc. work correctly with the monitor being driven at the selected resolution.

My xorg.conf is attached.

Ray

---

### Post by rzj on 2007-07-01
attachment failed. seems it didn't like .conf extensions

---

### Post by coffeecat on 2007-07-01
From your xorg.conf:

```
Section "Device"
    Identifier    "Intel Corporation 82945G/GZ Integrated Graphics Controller"
    Driver        "i810"
    BusID        "PCI:0:2:0"
EndSection
```I have a machine with the Intel 82845G video chipset and nothing I can do will make it display at greater than 1280x1024, whether in Linux using the i810 driver or Windows. Admittedly that's an earlier chipset than yours, but yours is a relatively old Intel chipset, so I wonder if you are running up against a similar limitation. I see that Windows is giving you 1680x1050 - if I read you correctly. Perhaps there is also some limitation in the i810 driver.

I believe there is a newer 'intel' xorg driver out now to replace the 'i810' one. I have no experience of this beyond trying an alpha version in another distro earlier this year which promptly crashed xorg for me. :( Nevertheless, you might wish to search for information on this driver to see if it might help.

Of course, I could be completely wrong. Sorry I can't offer anything more substantive.

**Edit:** By the way, the 'nv' and 'nvidia' drivers for nvidia cards and the 'via' driver for an onboard VIA graphics chipset all give me 1680x1050 quite easily in Feisty, unlike the Intel/i810 combination. I know this is no immediate help for you but I thought I would mention this because it shows how critical the chipset and/or xorg driver is when troubleshooting these issues

---

### Post by rzj on 2007-07-01
OK, I've found some stuff called 915resolution which seems to deal with this problem. It seems that there is a problem with the intel chipsets not reporting all of the modes they can handle so this package is used to overwrite an unused entry in the (I think) video bios with the values you need. I followed some instructions for Dapper, then subsequently found another page that said these instructions were out of date.

In the process of messing about I spotted the fact that the xorg.conf dislpay section which I had cribbed from another post on this forum about the ASUS monitor had a wierd set of display depths including 15 but not 32. Also that the chipset reports that it supports  8 16 and 32 - so not 24.

My xorg.conf had no 32 depth entry so I amended the 24 to 32 and changed default depth to 32.

In this state X cannot start, yet changing it back to 24 makes it work - don't understand this - why does 32 not work, and why is 24 ok if the chipset doesn't really do it?

Is there some setting elsewhere that is convincing X that it us running in 24 bit or that it needs to?

The error message on starting X said given depth (32) is not supported by I830 driver, and then that screens found but none have a usable configuration

Odd!

Still not getting a full screen display.

Ray

---

### Post by deepclutch on 2007-07-01
I'm sorry for the link(i left a")" ;) )
[http://gentoo-wiki.com/HOWTO_Widescreen_Resolutions_(WSXGA)]("http://gentoo-wiki.com/HOWTO_Widescreen_Resolutions_%28WSXGA%29")

---

### Post by rzj on 2007-07-01
Well I'm still not making much progress here!

I've tried quite a few variations from other people's xorg.conf files posted on the various sites liked to the asus monitor or the 915resolution tool.

In fact, apart from some changes stopping X from working and having to be undone, nothing seems to actually make a difference.

The fundamentally odd thing is that I get the impression that all these suggestions are to do with problems where the desired resolution is not available in the screen resolution selector, and the monitor is just not switching to the right settings.

In my case the monitor is driven correctly, it is just the displayed desktop that is not filling the full available width.

Ray

---

