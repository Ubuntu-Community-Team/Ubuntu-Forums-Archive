---
title: "Ubuntu won't recognize burnt discs"
date: 2009-05-01
forum: General Help
---

### Post by benhayman on 2009-05-01
I have an acer laptop which has been running on ubuntu for a year and a half now, and suddenly it won't run burnt or blank discs. If I put one it continues to make noises like it's trying to read the disc indefinitely.

If there is a disc in the computer when it boots up it will recognize that the disc is there and show the contents, but not be able to do anything with it, and if I take the disc out it'll continue to show the contents of the disc and not acknowledge that it's been ejected. It also doesn't recognize the disc while booting up apparently, since I tried this with a ubuntu boot disc and it booted normally.

Thanks in advance!

---

### Post by dandnsmith on 2009-05-01
Fairly typical behaviour of a particular type of CD-drive failure.

The powercycle/reboot gives sufficient impulse to the drive to get it to register the first track where the index is, but it never manages to go further or notice drawer open/close.

I've had this with several drives.

---

### Post by benhayman on 2009-05-01
So is that a "I need a new cd-drive" problem then? =[

[edit] Another question then, is there any other way I can change the operating system without a boot disc?

---

### Post by prem1er on 2009-05-01
> **benhayman said:**
> [edit] Another question then, is there any other way I can change the operating system without a boot disc?

Yes, if your computer supports it, you can boot from a flash drive for most linux distros.

---

### Post by benhayman on 2009-05-01
> **prem1er said:**
> Yes, if your computer supports it, you can boot from a flash drive for most linux distros.

Oh sweet, how do I do that?

---

### Post by dandnsmith on 2009-05-02
I'm afraid that you'll have to create the bootable flash drive for installation (see [www.pendrivelinux.com](www.pendrivelinux.com)), and then use (probably) F12 at boot to select the boot device.

Do you have the resources? The creation of the bootable USB is going to require download facilities, a stick of at least 1GB, and an operating system which is functional - these can be on a separate PC.

---

### Post by benhayman on 2009-05-02
OK, I have an 8gig flash drive, and access to another computer.

Also, what I'm trying to do is boot up with Windows XP on my laptop which currently runs Ubuntu.

---

### Post by dandnsmith on 2009-05-02
Sorry - you lost me.
Are you trying to (re)install XP, boot into an installation which is already there (but possibly not accessible).

I had the impression that you were wondering why the CDs wouldn't read, and then that you wanted to install Ubuntu.

---

### Post by benhayman on 2009-05-02
I'm trying to reinstall XP on a laptop that currently has Ubuntu, so when my burnt XP boot disc didn't work I experimented with other discs, including my ubuntu boot disc, trying to figure out the problem with the disc drive. Sorry for the confusion.

---

### Post by dandnsmith on 2009-05-03
Somewhere recently I've seen reference to installing XP from a USB stick - think it might have been in the [Acer Aspire One forums](http://www.aspireoneuser.com/forum/).

A technique I've used for earlier versions of Windows is to copy the installation CD content to the HDD (FAT partition) and install from there - I don't think this can be (easily) modified to using USB stick to install from (unless it is a bootable stick) because of the need to run under DOS.

HTH

---

### Post by fornix on 2009-05-03
Maybe this link would help
[http://articles.techrepublic.com.com/5100-22_11-5928902.html]("http://articles.techrepublic.com.com/5100-22_11-5928902.html")

---

