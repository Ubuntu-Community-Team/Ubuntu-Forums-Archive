---
title: "problems automounting usb key"
date: 2005-04-14
forum: Desktop Environments
---

### Post by tristure on 2005-04-14
Hi,

I'm still working on my fresh Kubuntu Hoary install.

On other problem I have concerns my USB key.

Actually it's a MP3 player/USB key (Creative MuVo 256Mo) ; but it behaves exactly like a USB key, except it's formatted in MSDOS format (I still can't understand why, but that's the way it is).

Now when I plug it in, the system detects it, here's the output of dmesg :
> usb-storage: device found at 3
usb-storage: waiting for device to settle before scanning
cx88[0]/0: AUD_STATUS: 0x6f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x772 [mono/no pilot] ctl=BTSC_AUTO_STEREO
  Vendor: Creative  Model: NOMAD MuVo TX     Rev: 0100
  Type:   Direct-Access                      ANSI SCSI revision: 04
usb-storage: device scan complete
SCSI device sda: 499968 512-byte hdwr sectors (256 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
SCSI device sda: 499968 512-byte hdwr sectors (256 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
 /dev/scsi/host0/bus0/target0/lun0: p1 

An icon appears on my desktop, as well as a /media/sda dir.

But if I try to open Konq on it, or just have a ls command, the CPU usage jumps to 100%, Konq keeps "waiting" and well, nothing happens, until I unplug the key (CPU back to "normal" usage, and konq closing).

Any idea about what can happen?

(PS : I have a "normal" ubuntu install on another partition, with Gnome, and the same thing happens, so I don't think it's exclusively KDE related)

Thanks!

---

### Post by Klin'Targ on 2005-04-14
Hmm I wonder if its mounting it as vfat instead of msdos for some reason. Try mounting it yourself manually before reading the directory. ```
mount -t msdos /dev/sda1 /media/sda1
```

A second observation: you said you have a "/media/sda" directory. This should be /media/sda# where # is the partition number. Trying to mount /dev/sda will result in badness, possibly the freeze you are experiencing.

---

### Post by !nkubus on 2005-04-14
[QUOTE=Klin'Targ]Hmm I wonder if its mounting it as vfat instead of msdos for some reason. Try mounting it yourself manually before reading the directory. ```
mount -t msdos /dev/sda1 /media/sda1
```

A second observation: you said you have a "/media/sda" directory. This should be /media/sda# where # is the partition number. Trying to mount /dev/sda will result in badness, possibly the freeze you are experiencing.[/QUOTE]


to know it just put the results of the following command :
```

sudo fdisk -l |grep sd 

```

it should give you something like this :
```

/dev/sda2   *           6         497     3951990    b  W95 FAT32

```


so we know where your device is.

as i see in your kernel messages 
```

 usb-storage: device found at 3

```
the usb key sould be at sda3, just try 
```

mount -t msdos /dev/sda3 /media/sda3

```

where 3 is the # of your partition in the command i gave you.

then after that try to acess it with the shell before to see if it's properly mounted.

Hope this helps  :)

ps. sorry for my bad english ;)

---

### Post by tristure on 2005-04-14
Thanks you both for your help.

Actually the device being found at 3 seems to have no relation with the number of the /dev/sda*, because it appears as /dev/sda1...

And if I mount it manually with a msdos  type, I can access it without any problem.

So my initial problem is partially solved.

To be perfectly happy I need two more things :
-the device to be automounted with the right type when I plug it in
-and the desktop icon to *NOT* appear, since I don't use desktop icons, it's useless.

If you have ideas how to do I'd be most grateful!
And don't worry about your english, mine is quite appalling too.  :grin:

---

