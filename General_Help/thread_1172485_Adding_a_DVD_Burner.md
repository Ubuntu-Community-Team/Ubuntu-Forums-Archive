---
title: "Adding a DVD Burner"
date: 2009-05-28
forum: General Help
---

### Post by stoneheart on 2009-05-28
I want to swap out an old CDRom reader for a DVDRW.  It's using the IDE/ATA interface and replacement physically should be easy.  However, do I have to do anything inside Ubuntu to get the new hardware to be recognized by Ubuntu.  I want to be able to use Brasero to burn to disk.

---

### Post by ajgreeny on 2009-05-28
It will normally be recognised at the next boot with no problem at all.

---

### Post by Bender2k14 on 2009-05-28
I was even able to swap a PCI video card for an AGP video card without any problems :)

---

### Post by VMC on 2009-05-28
> **stoneheart said:**
> I want to swap out an old CDRom reader for a DVDRW.  It's using the IDE/ATA interface and replacement physically should be easy.  However, do I have to do anything inside Ubuntu to get the new hardware to be recognized by Ubuntu.  I want to be able to use Brasero to burn to disk.

After you install it from a Terminal type the following to see for yourself:

```
wodim -checkdrive
```

---

### Post by DGortze380 on 2009-05-28
> **stoneheart said:**
> I want to swap out an old CDRom reader for a DVDRW.  It's using the IDE/ATA interface and replacement physically should be easy.  However, do I have to do anything inside Ubuntu to get the new hardware to be recognized by Ubuntu.  I want to be able to use Brasero to burn to disk.

Should be fine, check your cable jumpers.

---

### Post by khelben1979 on 2009-05-28
I recommend that you upgrade the firmware of the new DVD burner once you have it installed.

---

### Post by SunnyRabbiera on 2009-05-28
In any case it should work right away, Ubuntu and most modern linux distros have great hardware detection so most models should work right off the bat.
But BIOS might be another issue, sometimes you have to tweak the BIOS of your system a bit before certain devices become workable.

---

