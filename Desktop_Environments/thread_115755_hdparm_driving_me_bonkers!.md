---
title: "hdparm driving me bonkers!"
date: 2006-01-11
forum: Desktop Environments
---

### Post by kc2idf on 2006-01-11
I have a dual-boot Slackware/Ubuntu system.  HDD performance under Ubuntu was abysmal, so I looked into it.

Running hdparm /dev/hda from Slackware, I get:
/dev/hda:
 multcount    = 16 (on)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    =  8 (on)
 geometry     = 14593/255/63, sectors = 120034123776, start = 0

Running it under Ubuntu, I get:
/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 234441648, start = 0

...so I do some experiments.

I type: sudo hdparm -m16 -d1 -u1 -c1 /dev/hda

This gets me to:
/dev/hda:
 multcount    = 16 (on)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 234441648, start = 0

Also, while I am at it, I go into /etc/hdparm.conf, and add:
/dev/hda {
        io32_support = 1
        dma = on
        mult_sect_io = 16
        interrupt_unmask = on
}

So what results do I get?

1.  The entry in hdparm.conf has no effect, zero, zip, nada, zilch.  Every reboot (which, as you might suspect, are few), I have to manually issue the hdparm line to get the drive performance back up to snuff.

2.  Periodically (at least every 24 hours), the settings revert to the crappy settings.

Okay, guys, Ubuntu is supposed to be easy to use.... what obvious thing am I missing?

Oh, before I forget: system is a Via MII 12000 Mobo with a Western Digital 120GB ATA-100 HDD, 512MiB RAM, Via C3 Nehemiah core processor.

---

### Post by epostma on 2006-01-11
I don't know about the periodical resetting, but for booting:

Step 1. If you run the hdparm init script,
```
  $ sudo /etc/init.d/hdparm start
```
does it set the parameters correctly?

If yes -> check your startup links, 
```
ls -l /etc/rc?.d/*hdparm*
```
there should be a link from (probably) /etc/rcS.d/S07hdparm to  ../init.d/hdparm.

If no -> continue with these steps.

Step 2. Look at /etc/default/hdparm in addition to /etc/hdparm.conf; it should probably have no uncommented lines at all.

Step 3. What does it say if you ask
```
egrep -v '^[[:space:]]*(#|$)' /etc/hdparm.conf
```
It should be just the /dev/hda{...} block.

HTH,

---

### Post by kc2idf on 2006-01-27
I have fixed the problem by compiling a new kernel.  I started from the config of the stock kernel, went up one version (so as not to damage the stock collection of modules or the initrd) and made a couple of tweaks (changing processor, and making the IDE driver intrinsic rather than modular).  It now comes up right, and boots faster as a bonus.

---

