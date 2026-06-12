---
title: "Poor DVD Playback"
date: 2006-08-12
forum: Desktop Environments
---

### Post by Jheric on 2006-08-12
Ok, maybe I'm just spoiled. I tried FF7: Advent Children and and Batman Forever on Ogle, Mplayer, Totem, and VLC. I don't have a framerate problem and the colors are good. It's just that in any high motion sequences (especially camera movement) the video start to tear. It's not totally obvious but it like the horizontal is having trouble staying in sync. The drivers and libraries are whatever came on Automatix. 

Does anyone know what kind of settings are necessary to get the DVD playback to be as smooth as it is in Windows?

It's definately not a horsepower issue. This is a 2.4ghz, 1gb ram, 256mb video ram (nvidia) rig.

Thanks!

-Garrett

---

### Post by Anduu on 2006-08-12
I notice slight "tearing" as well...

Not sure about VLC but in MPlayer preferences there is an option to set the framerate...set it to something below your current refresh rate.

Haven't bothered to try it myself but it is worth a shot.

---

### Post by Jheric on 2006-08-13
Hmmm, changing the framerate just seemed to worsen play back. This is a bummer because now I can't overlook it... sigh...

---

### Post by Anduu on 2006-08-13
Well I just spent some time searching the forums and it seems there is no solution ....:(

---

### Post by Jheric on 2006-08-14
Thx for the help... same here.

I wonder if I can get power-dvd to run via wine....

-Garrett

---

### Post by llamakc on 2006-08-14
You've got hdparm set up for that drive, correct?

---

### Post by Anduu on 2006-08-14
DMA should be on by default in Dapper...

Its actually not a lack performance issue...rather a too much performance issue ;)

---

### Post by llamakc on 2006-08-14
Really? Here's mine:

```

root@dothan:/home/ken# hdparm /dev/hdd

/dev/hdd:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

```

The file /etc/hdparm.conf does NOT have the /dev/cdrom set up by default.

---

### Post by Anduu on 2006-08-14
That is odd because my CDRW,DVD and DVDRW are all on...fresh install too...:-k

Correction the DVDRW is usb so no DMA option there...

---

### Post by stdragon on 2006-08-14
Hey take a look at "mplayer -vo help" and try a few different options. For instance to try open-gl output which may help, try

mplayer -vo gl dvd://

You can also try mplayer's filters (in case this is actually interlacing that you're seeing). Try mplayer -vf pp=fd dvd:// or mplayer -vf pp=de dvd:// and see if there's any improvement.

---

