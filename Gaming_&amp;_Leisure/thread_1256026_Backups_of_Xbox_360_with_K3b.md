---
title: "Backups of Xbox 360 with K3b"
date: 2009-09-02
forum: Gaming &amp; Leisure
---

### Post by TrUkvk on 2009-09-02
Hi!!
I've just registered and this is my first post. I hope this is the correct place for this question, otherway, please let me know and sorry ^^

My problem is:
I've been trying to burn Xbox 360 backups with K3b because I read it was extremely easy. And of course it is, I changed the preferences adding "-use-the-force-luke=break:1913760" at the growisofs line, but when I try to burn this is what I get:

[B][I]System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.28-12-generic
Devices
-----------------------
Optiarc DVD RW AD-7560S SX07 (/dev/sr0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R secuencial, DVD-R Doble capa secuencial, DVD-R doble capa salteado, DVD-RAM, DVD-RW sobreescritura restringida, DVD-RW secuencial, DVD+RW, DVD+R, DVD+R doble capa, CD-ROM, CD-R, CD-RW] [SAO, TAO, En bruto, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Sobrescritura restringida, Salto de capa]

Burned media
-----------------------
DVD+R doble capa

Used versions
-----------------------
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr0 obs=32k seek=0'
  Failed to change write speed: 2770->3324
/dev/sr0: splitting layers at 1913760 blocks
/dev/sr0: "Current Write Speed" is 2.5x1352KBps.
          0/7838695424 ( 0.0%) @0x, remaining ??? RBU 100.0% UBU   0.0%
          0/7838695424 ( 0.0%) @0x, remaining ??? RBU 100.0% UBU   0.0%
          0/7838695424 ( 0.0%) @0x, remaining ??? RBU 100.0% UBU   0.0%
          0/7838695424 ( 0.0%) @0x, remaining ??? RBU 100.0% UBU   0.0%
          0/7838695424 ( 0.0%) @0x, remaining ??? RBU 100.0% UBU   0.0%
          0/7838695424 ( 0.0%) @0x, remaining ??? RBU 100.0% UBU   0.0%
          0/7838695424 ( 0.0%) @0x, remaining ??? RBU 100.0% UBU   0.0%
          0/7838695424 ( 0.0%) @0x, remaining ??? RBU 100.0% UBU   0.0%
          0/7838695424 ( 0.0%) @0x, remaining ??? RBU 100.0% UBU   0.0%
          0/7838695424 ( 0.0%) @0x, remaining ??? RBU 100.0% UBU   0.0%
          0/7838695424 ( 0.0%) @0x, remaining ??? RBU 100.0% UBU   0.0%
          0/7838695424 ( 0.0%) @0x, remaining ??? RBU 100.0% UBU   0.0%
          0/7838695424 ( 0.0%) @0x, remaining ??? RBU 100.0% UBU   0.0%
          0/7838695424 ( 0.0%) @0x, remaining ??? RBU 100.0% UBU   0.0%
          0/7838695424 ( 0.0%) @0x, remaining ??? RBU 100.0% UBU   0.0%
          0/7838695424 ( 0.0%) @0x, remaining ??? RBU 100.0% UBU   0.0%
          0/7838695424 ( 0.0%) @0x, remaining ??? RBU 100.0% UBU   0.0%
:-[ WRITE@LBA=0h failed with SK=0h/ASC00h/ACQ=03h]: Input/output error
  write failed: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/sr0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:3827488 -dvd-compat -speed=2.4 -use-the-force-luke=bufsize:32m -use-the-force-luke=break:1913760 [/I][/B]

The thing is that, last night, desperate, I tried one more time and... SURPISE!! It worked.

You have any ideas?

Thanks a lot.


EDIT: I include an image of the error and the config

[IMG]http://i258.photobucket.com/albums/hh242/trukvk/Pantallazo-GrabandoimagenISO9660-K3.png[/IMG]

[IMG]http://i258.photobucket.com/albums/hh242/trukvk/Pantallazo.png[/IMG]

---

### Post by TrUkvk on 2009-09-09
Please I need help, you don't have any ideas?

---

### Post by joeelmex on 2009-09-09
I don't think you will get support on burnng back up games for the xbox 360 on here.

---

### Post by TrUkvk on 2009-09-09
Maybe any of you know...

---

### Post by disturbedite on 2009-09-09
*i could be wrong*, but i've never heard that k3b supports or has ever supported copying/burning xbox 360 discs.

---

### Post by Nevon on 2009-09-09
While it *should* work in K3B, I suggest you try the following command instead:
```
growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760 -dvd-compat -speed=2 -Z /dev/dvd=~/FULL/PATH/TO.ISO
```

Or, if you prefer to do it graphically, download this script: [http://www.blastfromthepast.se/blabbermouth/2009/04/how-to-burn-xbox-360-isos-in-linux/](http://www.blastfromthepast.se/blabbermouth/2009/04/how-to-burn-xbox-360-isos-in-linux/)

---

### Post by TrUkvk on 2009-09-10
It worked witn that sentence thanks. The strange thing is that K3b worked sometimes... In fact, I've burned 2 games with it ant they worked perfect.

---

### Post by Saghaulor on 2009-10-09
I've had issues burning dvd's using gui's. So I just do it from the CLI now. I don't really have issues anymore since the switch.

It takes a lil more effort, but the results pay off better.

Btw, are the copies successful? I'd like to backup my stuff as well, as my girlfriend and I are not the most delicate on media, so I'd much rather scratch a backup all to hell than the original media.

---

### Post by Nevon on 2009-10-09
> **Saghaulor said:**
> Btw, are the copies successful? I'd like to backup my stuff as well, as my girlfriend and I are not the most delicate on media, so I'd much rather scratch a backup all to hell than the original media.

If you have a flashed Xbox, you can play your own backups. On an unmodded Xbox, you cannot. Also, I believe doing so is in violation of whatever agreement you were forced into when purchasing your console.

---

### Post by Dimitriid on 2009-10-09
The only guides and tutorials I've found for such tasks are for imgburn which is very usable under wine ( you just might need to open the program first, then open winecfg to manually mount the blank media ).

---

### Post by Dimitriid on 2009-10-09
> **Nevon said:**
> If you have a flashed Xbox, you can play your own backups. On an unmodded Xbox, you cannot. Also, I believe doing so is in violation of whatever agreement you were forced into when purchasing your console.

That is only applicable in certain countries, in my country for example the 360 is sold and officially supported yet is perfectly legal to modify it in any way and play any back up games I want so long as there is no profit ( and we define profit as actual currency being exchange for copyrighted material and that's it ).

---

### Post by Nevon on 2009-10-10
> **Dimitriid said:**
> That is only applicable in certain countries, in my country for example the 360 is sold and officially supported yet is perfectly legal to modify it in any way and play any back up games I want so long as there is no profit ( and we define profit as actual currency being exchange for copyrighted material and that's it ).

Modding it is not illegal in any country, as far as I know. But it does breach the user agreement.

> **Dimitriid said:**
> The only guides and tutorials I've found for such tasks are for imgburn which is very usable under wine ( you just might need to open the program first, then open winecfg to manually mount the blank media ).

There's no need to use imgburn in wine. You can just use the command I posted above. Or if you'd rather use a graphical front-end, simply paste the arguments supplied into k3b - as the OP had done in the screenshot.

---

