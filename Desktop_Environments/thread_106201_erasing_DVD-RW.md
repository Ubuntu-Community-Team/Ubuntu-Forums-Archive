---
title: "erasing DVD-RW"
date: 2005-12-20
forum: Desktop Environments
---

### Post by GrumpyBob on 2005-12-20
I have Ubuntu Breezy on and IBM Thinkpad.  I cannot erase DVD-RW discs when burning data to them via Nautilus.  When used on the command line, cdrecord throws a bit of a wobbly, something is missing from the installation.    

I can erase the disc using K3B, but would rather do it through Nautilus for convenience.

Is this a standard issue for which there's a fix?  Sorry I can't post error messages, I'm at my work WinXP box!

Robert

---

### Post by earobinson on 2005-12-20
what about gnomebaker, I know you want to use Nautilus, but gnomebaker is gnome based

---

### Post by GrumpyBob on 2005-12-20
I will try later, when I get home.  

I tried:
sudo umount /dev/cdrom
cdrecord dev=/dev/cdrom blank=fast
(from the unofficial 5.04 guide)

But having googled cdrecord, I wonder if this is correct for a DVD-RW.  Would 
cdrecord dev=/dev/cdrom format
work better for DVD-RW?  I'll give it a whirl tonight, and investigate Nautilus settings.

Robert

---

### Post by earobinson on 2005-12-20
my guess Is that this is not a feature that Nautilus has added yet

---

### Post by GrumpyBob on 2005-12-20
You may well be right.  I've just been googling to see what Natilus uses for CD/DVD writing, the Nautilus home page seems surprisingly light on information, more searching is obviously in order...

Edit:  Nautilus is quite happy burning DVD-RWs, it's just unable (at least on my laptop) to erase them for rewriting.  I can write to the DVDs if I erase them on Windows, or using K3B.

Robert

---

### Post by earobinson on 2005-12-20
gnomeburner should be able to erase dvds, check it out.

---

### Post by Irony on 2005-12-20
I can erase CD-RW but not DVD+RW.

It would be useful if Ubuntu could use RW discs like nero does them, i.e. writing to them like they were just another drive (a super floppy).

---

### Post by earobinson on 2005-12-20
who knows maybe its comming in dapper

---

### Post by dcstar on 2005-12-20
[QUOTE=Irony]I can erase CD-RW but not DVD+RW.

It would be useful if Ubuntu could use RW discs like nero does them, i.e. writing to them like they were just another drive (a super floppy).[/QUOTE]
Do you have dvd+rw-tools installed?

BTW, I use UDF CD-RWs and can write to them just as I did in Windows (install udftools).....

I have my UDF disk mounted automatically on start-up, and write to it no problems at all.

There are a few issues with setting it all up, but it is worth it. I still haven't got this working with a DVD+RW disk, but I'm happy just having the functionalty with a CD-RW!

---

### Post by earobinson on 2005-12-20
good to know

---

