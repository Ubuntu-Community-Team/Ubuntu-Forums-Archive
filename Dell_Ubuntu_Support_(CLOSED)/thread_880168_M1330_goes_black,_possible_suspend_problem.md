---
title: "M1330 goes black, possible suspend problem"
date: 2008-08-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by antiOST on 2008-08-04
Hi

Just experienced that my laptop goes black when I'm not using, it has done this twice tonight. I left it turned on (not even closing the lit) cause I was doing som filetranfers to a computer on LAN and some download from the net (and properly running firefox).

The Screen is black but if i press the power button, I can hear the laptop's still "working"

the device lights for Caps Lock and Scroll lock is blinking  simultaneous (the second and third light to the left the media direct button) 

I'm running Gusty on a M1330 and have never experienced this before (even when I've left the laptop turned on without using it for days)

I haven't been messing with suspend og standby but the symptoms could loke like its suspended and cant come back.

I have to turn off completely and start up to get any reactions...

-Kim

---

### Post by superm1 on 2008-08-04
> **antiOST said:**
> Hi

Just experienced that my laptop goes black when I'm not using, it has done this twice tonight. I left it turned on (not even closing the lit) cause I was doing som filetranfers to a computer on LAN and some download from the net (and properly running firefox).

The Screen is black but if i press the power button, I can hear the laptop's still "working"

the device lights for Caps Lock and Scroll lock is blinking  simultaneous (the second and third light to the left the media direct button) 

I'm running Gusty on a M1330 and have never experienced this before (even when I've left the laptop turned on without using it for days)

I haven't been messing with suspend og standby but the symptoms could loke like its suspended and cant come back.

I have to turn off completely and start up to get any reactions...

-Kim
This is a kernel panic.  I know there were some stability issues with the wireless drivers in Gutsy, so you may consider upgrading to hardy.

---

### Post by antiOST on 2008-08-05
Thanks,

Was already thinking of upgrading, but since Dell announced that the are going hardy so I think I'll wait for their image.

-Kim

---

### Post by superm1 on 2008-08-05
> **antiOST said:**
> Thanks,

Was already thinking of upgrading, but since Dell announced that the are going hardy so I think I'll wait for their image.

-Kim
There are some technical complications with the creation of hardy ISOs at this point.  At least for the M1330, there are *no* added things in the Dell hardy ISO that you will need other than the new recovery partition setup.  Everything else is in the archive via hardy-updates.

---

### Post by antiOST on 2008-08-05
Ok, nice to know, I'll give a second thought then.

thanks
Kim

---

### Post by ole8000 on 2008-08-23
Yesterday I got same error with blinking lights under hardy:

I went to bed and started file transfer for fedora dvd image (via wlan and router), and after about 2 minutes screen went black and lights were blinking.

I get this error under many distributions and kernels when installing cisco systems vpn client and running it over a wlan connection, it randomly gets into kernel panic. vpnc works fine (at least no panic til now).

Maybe it's really a problem with the wlan. Using original hardy image on m1330.

--ole8000


(PS Do bridge-utilities and uml-utitlities add any modules? I installed them yesterday for vbox host networking, but didn't change anything to the config. was the only thing i changed yesterday, removed them now)

---

