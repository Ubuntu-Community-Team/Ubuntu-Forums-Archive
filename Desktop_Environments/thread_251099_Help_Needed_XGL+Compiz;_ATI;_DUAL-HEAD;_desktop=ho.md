---
title: "Help Needed: XGL+Compiz; ATI; DUAL-HEAD; desktop=horizontal"
date: 2006-09-04
forum: Desktop Environments
---

### Post by RyanTMulligan on 2006-09-04
Hi I'm trying to XGL to work with my ATI in the big desktop mode.

I have confirmed that big desktop and fglrx works for me without XGL.
I have also confirmed that XGL works when I am in single screen one monitor mode.

However, now I'm trying to get them both to work.

So first I do...
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.single-screen-back
```
```
aticonfig --dtop=horizontal --overlay-on=1
```

I then restarted GDM.
```
 /etc/init.d/gdm restart
```
This resulted in GDM trying to start 4 times, but crashing each time after about waiting a minute. I checked the logs then an this it what I saw.
```
 (EE) fglrx(0): === [R200DALGetControllerInfo] === CWDDC ControllerGetConfig failed: 6 
(EE) fglrx(0): === [R200DALGetControllerInfo] === CWDDC ControllerGetConfig failed: 6

```

I then read this [post]("http://ubuntuforums.org/showthread.php?t=187074")

Which convinced me to add Option "nodri" to my ATI Device like so...
```

Section "Device"
   Identifier "ATI Technologies, Inc. R420 JI [Radeon X800PRO]"
   Driver "ati"
   Option "nodri"
   BusID  "PCI:1:0:0"
EndSection

```

So I did that and it worked a little better now. Instead of restarting X 4 times, it just sat there at a the white noise screen with the ubuntu waiting mouse.

I then went to the console and type Xgl and this is what I saw...

```
 
Various X stgartup scripts... moving into the Xorg.conf...

(==) Using config file: "/etc/X11/xorg.conf/"
(WW) fglrx: No Matching Device section for instance (BusID PCI:1:0:1) found
(EE) fglrx(0): === [R200DALGetControllerInfo] === CWDDC ControllerGetConfig failed: 6 
(EE) fglrx(0): === [R200DALGetControllerInfo] === CWDDC ControllerGetConfig failed: 6

```
And it seems like Xgl just hung there.

Does anyone have any advice on this?

---

