---
title: "Playstation (PSX) CD hangs"
date: 2007-04-29
forum: Gaming &amp; Leisure
---

### Post by EEVOL on 2007-04-29
I recently upgraded (new install) to Feisty on my Toshiba M35-S359 laptop.  In addition I also have ePSXe installed.  Now every time I put in a PSX CD, it just hangs and I'm not able to eject the cd -- this happens on all original PSX cds.  At this point I'm still able to do other things but ejecting the CD.  Does anyone know what could possibly be wrong with this or have some sort of fix for it?  Thanks in advance.

---

### Post by po0f on 2007-04-29
EEVOL,

How do you have optical drives configured in ePSXe?  Are you using a plug-in?  If so, which one?  I haven't used ePSXe in a while, so I can't help with specific details.

Also, note that in Feisty, all drives are handled by the kernel's SCSI system; your first optical drive (normally /dev/hdc) is probably named /dev/scd0.

HTH

[EDIT]

You may find that ripping your PSX games to disk makes playing games a little more manageable.  A script is provided in the link below (shameless self-promotion):

[CLICK](http://ubuntuforums.org/showthread.php?p=1982830#post1982830)

[EDIT 2]

As mentioned above about Feisty's kernel using the SCSI system for drives, you will have to edit the script a little; you'll have to change the line:

```
cdrdao read-cd --device ATA:1,0,0 --driver generic-mmc-raw --read-raw --datafile $1.bin $1.toc
```

to:

```
cdrdao read-cd --device 1,0,0 --driver generic-mmc-raw --read-raw --datafile $1.bin $1.toc
```

assuming you want to use the first optical drive.

---

