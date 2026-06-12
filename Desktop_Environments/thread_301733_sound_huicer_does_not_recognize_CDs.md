---
title: "sound huicer does not recognize CDs"
date: 2006-11-17
forum: Desktop Environments
---

### Post by RikoW on 2006-11-17
Hi all,

it seems like sound juicer is not able to resolve the CD info anymore from a CDDB. Whenever I put in a CD, I only get unknow artist, unknow album and tracks just labeled as "tack 01" etc.

On the other hand, when I use grip to rip a CD, it does recognize the cd content properly and retrieves the proper track and album info.

Anybody experiencing something similar? Or maybe even has a solution for it?

Thanks and cheers,

                 Riko

---

### Post by mitch.c on 2006-11-17
> **RikoW said:**
> Hi all,

it seems like sound juicer is not able to resolve the CD info anymore from a CDDB. Whenever I put in a CD, I only get unknow artist, unknow album and tracks just labeled as "tack 01" etc.

I don't know for how sound-juicer gets the info, but I suspect it's via  CDDB-Slave2. Can you use gconftool-2 to check these values (output from my system listed)?
```
$ gconftool-2 --get /apps/CDDB-Slave2/port
8880

$ gconftool-2 --get /apps/CDDB-Slave2/server
freedb.freedb.org

$ gconftool-2 --get /apps/CDDB-Slave2/server-type
0
```
If the values are wrong, you can use gconftool-2 to set them; gconftool-2 is available in the gconf2 package. For a GUI, install the gconf-editor package.

---

### Post by RikoW on 2006-11-18
Hi,

I get the same values as you ....

---

### Post by my3ke on 2006-12-01
The first page of the HELP under Introduction says it uses MusicBrainz for it's lookups.  I too seem to have the same issue with sound juicer.  When I use GRIP (which I like better) I can rip one of my cds and the next one I rip after it hoses the machine.  I have to cold boot the beast.  I'm using Ubuntu 6.06.

---

### Post by my3ke on 2006-12-01
Okay, I've been toying with SJ trying to figure out how it picks up it's track information to see if maybe my firewall was stopping it.

I had a CD in and had it Re-Read Disk (control-R) and it found the tracks and  album info.  Since then, I've tried a few other CDs and now it updates itself.

So maybe drop a disc in and convince it to cooperate with a Re-Read Disc command?

my3ke

---

