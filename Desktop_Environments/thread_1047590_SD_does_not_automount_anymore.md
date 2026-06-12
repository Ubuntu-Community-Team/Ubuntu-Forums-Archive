---
title: "SD does not automount anymore"
date: 2009-01-22
forum: Desktop Environments
---

### Post by jemdos on 2009-01-22
Greetings from Sunny Spain 8)

I've recently reformated on my Palm TX a 1GB Kingston SD Card. I've always mounted it on my Ubuntu 7.10 box without any troubles, just inserting it on the slot of my card reader. But since I reformated it, I cannot:
1. I can mount it on hand, from console. But it does not automount. 
2. It automounts the rest of my SD cards, it's just this one it refuses to mount automatically.
3. It does automount on another Ubuntu machine (the SD reader card is the same, it plugs on an usb slot)
4. The SD card does mount on Windows on the same machine I cannot automount using Ubuntu.

So something strange is happening on gnome level, but I dunno what.

Help, I am absolutely clueless about what to do.

---

### Post by jerome1232 on 2009-01-22
I'm just shooting in the dark for an error here but when you plug it in does dmesg say anything?

plug it in, then do this

```
cat /var/log/dmesg | tail
```

---

### Post by jemdos on 2009-01-23
Thanx for answering.

I see no differences on dmesg output, no matter what a do to the card. I can see that's /dev/sdc (two SATA hard drives are sda and sdb). I just think something is preventing gnome (not linux) from mounting the device and showing it accordingly *with this sd card*.

I've also checked lshal and there's no difference I am aware no matter I've plugged in the "no automounting" sd card or a "no trouble at all" sd cards.

And this sd card loads faultlessly on other computers and OSes, including ubuntu on another box.

So I think there's something rotten on some log file or so. I've checked also the .mtab files on /media, but they look ok to me.

This is driving me /dev/nuts.

cat /var/log/dmesg | tail
1. Before plugging in the sd card

[   52.438963] usbcore: registered new interface driver visor
[   52.438968] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver
[   52.542842] it87: Found IT8712F chip at 0x290, revision 5
[   52.583450] Adding 2048276k swap on /dev/sdb2.  Priority:-1 extents:1 across:2048276k
[   52.587897] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   52.588234] EXT3 FS on sdb1, internal journal
[   53.238098] kjournald starting.  Commit interval 5 seconds
[   53.238106] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   53.238434] EXT3 FS on sdb3, internal journal
[   53.238438] EXT3-fs: mounted filesystem with ordered data mode.

Last lines are about me preventing disk checking while boot. Very annoying. 8)

2. After plugging in the sd card
[   52.438963] usbcore: registered new interface driver visor
[   52.438968] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver
[   52.542842] it87: Found IT8712F chip at 0x290, revision 5
[   52.583450] Adding 2048276k swap on /dev/sdb2.  Priority:-1 extents:1 across:2048276k
[   52.587897] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   52.588234] EXT3 FS on sdb1, internal journal
[   53.238098] kjournald starting.  Commit interval 5 seconds
[   53.238106] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   53.238434] EXT3 FS on sdb3, internal journal
[   53.238438] EXT3-fs: mounted filesystem with ordered data mode.

3. After mounting sd card using the console (sudo mount etc)

[   52.438963] usbcore: registered new interface driver visor
[   52.438968] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver
[   52.542842] it87: Found IT8712F chip at 0x290, revision 5
[   52.583450] Adding 2048276k swap on /dev/sdb2.  Priority:-1 extents:1 across:2048276k
[   52.587897] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   52.588234] EXT3 FS on sdb1, internal journal
[   53.238098] kjournald starting.  Commit interval 5 seconds
[   53.238106] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   53.238434] EXT3 FS on sdb3, internal journal
[   53.238438] EXT3-fs: mounted filesystem with ordered data mode.

4. Inserting a different card (ubuntu notices it at once, and puts a "disk" icon on m desktop, so it mounts the device without any problem):

[   52.438963] usbcore: registered new interface driver visor
[   52.438968] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver
[   52.542842] it87: Found IT8712F chip at 0x290, revision 5
[   52.583450] Adding 2048276k swap on /dev/sdb2.  Priority:-1 extents:1 across:2048276k
[   52.587897] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   52.588234] EXT3 FS on sdb1, internal journal
[   53.238098] kjournald starting.  Commit interval 5 seconds
[   53.238106] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   53.238434] EXT3 FS on sdb3, internal journal
[   53.238438] EXT3-fs: mounted filesystem with ordered data mode.

---

