---
title: "How to make bootable floppy from Live CD?"
date: 2009-02-25
forum: General Help
---

### Post by MountainX on 2009-02-25
I have booted Ubuntu from the 8.10 Live CD. Now I want to make a bootable floppy disk.

The process fails at the first step:
```
mke2fs /dev/fd0
```

error is ```
could not stat /dev/fd0 --- no such file or directory
```

what is wrong?

SOLVED:
sudo modprobe floppy

---

### Post by mb_webguy on 2009-02-26
Um... you're talking about a 1.5MB floppy?  You realize you'd be hard-pressed to put a single mp3 on one of those, right?  You're certainly not going to be able to put Ubuntu on one.  Even Damn Small Linux is 50MB.

There are a few distributions of Linux designed to do what you're doing, but... don't expect much more than the kernel and a shell.  A few I found with a quick Google search are [LOAF]("http://www.linuxdevices.com/links/LK8414188089.html") (Linux On A Floppy), [SPYLinux]("http://www.advogato.org/proj/spyLinux/") (Small Python Linux), and [Xwoaf]("http://modest-proposals.com/Hacklin.htm") (X-Windows On A Floppy).

---

### Post by MountainX on 2009-02-26
> **mb_webguy said:**
> Um... you're talking about a 1.5MB floppy? 

[https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)

maybe I should have specified that I wanted to make a grub boot floppy. Anyway, the steps at the link above worked once I discovered how to modprobe floppy

---

### Post by mb_webguy on 2009-02-26
> **MountainX said:**
> [https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)

maybe I should have specified that I wanted to make a grub boot floppy. Anyway, the steps at the link above worked once I discovered how to modprobe floppy

Oooohhh.  Yeah, that makes a difference!  A GRUB boot floppy is a bit different from making a bootable Linux floppy.  I'm glad you figured it out.  Sorry for the confusion.

---

### Post by MountainX on 2009-02-26
I never thought about booting an actual Linux OS entirely from a floppy, but some of those links you provided look really cool. I might have to try that. Or at least maybe I'll try Puppy Linux from a memory stick.

But for now, the grub boot disk really saved me a lot of trouble!

---

