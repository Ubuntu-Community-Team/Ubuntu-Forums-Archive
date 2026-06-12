---
title: "Burning an .iso"
date: 2006-02-16
forum: Desktop Environments
---

### Post by montes.c on 2006-02-16
How can I burn an .iso ? I right clicked and selected to burn, but it keeps asking for a blank cd, I put a brand new blank cd and it still asks the same, no matter how many brand new blank cds I try.

---

### Post by taurus on 2006-02-16
Are you trying to burn it in Windows or Ubuntu???  If you use Windows, then fire up nero and tell it to burn it as image file, NOT data file.  But if you use Ubuntu, then you can use k3b and do the same thing.  In ther words, you need to burn your ISO as an image file so you can be able to boot from it.  But if you decide to burn it as a data file, then you are basically just copying it to your CD, wasting time and CD because you can't boot from it!

---

### Post by bored2k on 2006-02-16
> **Burning an iso-image**

To burn an iso-image run (replace /dev/hdc with the name of your recording device):

```
cdrecord -v dev=/dev/hdc isoimage.iso
```


**Burning a bin/cue**

To burn a bin/cue image run (replace /dev/hdc with the name of your recording device):

```
cdrdao write --device /dev/hdc image.cue
```

> 
**Burning DVDs from ISO Image Files**

To burn a DVD from an ISO image use:

```
growisofs -Z /dev/cdrw=/path/to/iso
```Should work.

---

### Post by montes.c on 2006-02-16
How do I know what is the name of my recording advice?

I dont know if it is /dev/hdc or not.

---

### Post by bored2k on 2006-02-16
```
cat /etc/fstab
```
It's the one device pointing to your /media/cdrom0 or so.

---

### Post by wayward on 2006-06-22
[QUOTE=montes.c]How do I know what is the name of my recording advice?

I dont know if it is /dev/hdc or not.[/QUOTE]


Try running

cdrecord -scanbus

---

### Post by Kuraboy on 2006-06-24
Hi!

why dose it tell me that this cdrecord isnt the original version, and it have unsetteled issues with Linux 2.5 and newer?!
 :confused:

---

