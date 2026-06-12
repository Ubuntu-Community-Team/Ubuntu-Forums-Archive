---
title: "Compiz NOT Working in 9.04 !"
date: 2009-04-24
forum: Desktop Environments
---

### Post by Anquietas on 2009-04-24
Hello,

I like Ubuntu very much, I want it to give it to my friends and colleagues, but... there is a problem.

In 8.10, Compiz and Desktop Effects worked great with my Intel Card.

Now, when I wish to active the effects, it says

```
Desktop effects could not be enabled
```

Here is the output of "lspci"
```

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

```

I've already commented out the Blacklisted Cards in /usr/bin/compiz.
I've tried to use "SKIP_CHECKS=YES", it still won't load.
It complaints about not detecting a Display.

Another code:
```

root@tehnic:~# glxinfo |grep direct
Error: unable to open display 
root@tehnic:~#

```

Please advice, there must be something wrong with Jaunty. in Intrepid it worked, in Jaunty it doesn't work... that is all I know.

---

### Post by gettinoriginal on 2009-04-25
Sometimes when updating or upgrading the video driver gets changed.  Go to System > Admin > Hardware drivers and make sure the correct driver is activated.  Once that is done, check System > Preferences > Appearance > Visual Effects that it is set to "Normal", "Extra", or "Custom".  :P

---

### Post by andrea000 on 2009-04-26
You may want to check and see if your chip set has been blacklisted
but try what gettinoriginal said first that would be what i would try
first.

---

