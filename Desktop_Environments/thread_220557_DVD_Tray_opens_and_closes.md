---
title: "DVD Tray opens and closes"
date: 2006-07-21
forum: Desktop Environments
---

### Post by patrickthebold on 2006-07-21
Sort of a wierd annoyance:  I just got a dvd burner and I am using Nautilus 2.14.1 to burn the iso images.  Right click, burn to disc.  It works fine, but when it's finnished it opens the dvd tray and then immediately closes it.  Is there anyway to make this stop?   

possible relavant info.

dvd drive from dmesg: hdd: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)

dmesg doesnt seem to have anything relevent when the "problem" occurs.


$ cat /proc/sys/dev/cdrom/info
CD-ROM information, Id: cdrom.c 3.20 2003/12/17

drive name:             hdd     hdc
drive speed:            48      24
drive # of slots:       1       1
Can close tray:         1       1
Can open tray:          1       1
Can lock tray:          1       1
Can change speed:       1       1
Can select disk:        0       0
Can read multisession:  1       1
Can read MCN:           1       1
Reports media changed:  1       1
Can play audio:         1       1
Can write CD-R:         1       1
Can write CD-RW:        1       1
Can read DVD:           1       0
Can write DVD-R:        1       0
Can write DVD-RAM:      1       0
Can read MRW:           0       1
Can write MRW:          0       1
Can write RAM:          1       1

---

### Post by orb9220 on 2006-07-21
Don't think so it's probally a imbedded function of nautilus.

Wht is doing is ejecting and closing so it can mount and remount.

And yes it is very annoying when coping cd/dvd to have the disk which it just finished to open and close again before you can eject it.

Why is this and can we stop it?

---

### Post by jrjr on 2006-07-21
I just burned the server iso by right clicking in Nautilus and saying write to disk. When it was done the prompt came up and it just sat there. Did not open the tray till I told it to. Worked good. Guess that means its not something inherent with Nautilus eh?

---

### Post by scxtt on 2006-07-21
i'm pretty sure that happens to me w/ my DVD-ROM -- honestly, i don't care too much - what's that, 3 seconds of my life 'waiting'? ...

---

### Post by orb9220 on 2006-07-21
Not really its 3 seconds to open 5 secs to read and mount 3 more seconds to eject then put in disk wait another 3-5 secs for it to mount then click ok button to start the burn so it is not just 3 secs.

---

### Post by scxtt on 2006-07-21
:rolleyes:

---

### Post by patrickthebold on 2006-07-23
So does anyone know how to configure nautilus to see what it is calling and perhaps modify it?  The preferences seem to offer no help, but there must be some way to configure it.

---

### Post by orb9220 on 2006-07-24
Maybe this. Not sure run the gconf-editor in term or from menu 
then look in apps>gnome-cd there is an entry that says on-stop-eject that is unchecked.

description is:

Eject the CD when CD player quits?
Should the CD be ejected when the CD player quits?

Quits what not clear what it does. But if there is any place for chosing default behavior this must be the place.

---

### Post by jethro10 on 2006-07-24
This also happened to me a few months ago.
It started near the end of the Dapper testing cycle just before the final release and I guess some update caused it. It is strange.
It also broke some other methods of writing Optical drives but I just work round them.


J

---

