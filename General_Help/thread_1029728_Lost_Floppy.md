---
title: "Lost Floppy"
date: 2009-01-03
forum: General Help
---

### Post by banishmemory on 2009-01-03
Hello everyone!
I have installed Ubuntu 8.10 x86 and M$ XP (32 bits) on my PC.
I have 3.5" floppy drive, and it is no problem to use in in XP but in Ubuntu it just "doesn't exist".
I tried:
```
mount /media/floppy
```
but I receive following error:
```
mount: special device /dev/fd0 does not exist
```
My kernel version is: **2.6.27-9-generic**.

Any ideas? :confused:

---

### Post by Tim Sharitt on 2009-01-03
Try
```
sudo modprobe floppy
```
and then try mounting it.

If it works you can add floppy to /etc/modules to have it load every time.

---

### Post by banishmemory on 2009-01-04
Thanks! It works! [IMG]http://k43.pbase.com/u22/johnsgallery/upload/20583285.beer.gif[/IMG]

---

