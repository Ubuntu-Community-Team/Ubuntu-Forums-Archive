---
title: "Format Cd-rw"
date: 2004-12-13
forum: Desktop Environments
---

### Post by rmdnet on 2004-12-13
Hi,

How would you format a CD-RW?

I want to use it as a usual cd, that is, writing once, blanking all the cd and so on. I don't mind if I can't use it like a floppy.

Would you use k3b and make a full format the first time?. Or maybe something similar to cdrwtool?

Thanks a lot

Rmdnet

---

### Post by randy on 2004-12-13
From the command line you can user cdrecord.  Execute
 cdrecord dev=cdburnerdevice blank=all

---

### Post by jdong on 2004-12-13
If you're talking about UDF Packet Writing (i.e. InCD, DirectCD, Drag-to-Disc), the support isn't in Ubuntu's default kernel. It's in some patchsets, like -mm and -ck.

I don't recommend you use CD-RW's in this way. It seriously cuts down on their life, plus I can't tell you HOW MANY times I've experienced corruption with InCD or DirectCD!!

Through Nautilus-cd-burner and K3b, it's easy enough to master a CD -- just as easy as dragging files anywhere else.

If you would like to use the CD like a floppy, then **maybe you're better off with a USB stick**, or something else that is great for  countless read-writes!

---

### Post by rmdnet on 2004-12-14
[QUOTE=jdong]If you're talking about UDF Packet Writing (i.e. InCD, DirectCD, Drag-to-Disc), the support isn't in Ubuntu's default kernel. It's in some patchsets, like -mm and -ck.

I don't recommend you use CD-RW's in this way. It seriously cuts down on their life, plus I can't tell you HOW MANY times I've experienced corruption with InCD or DirectCD!!

Through Nautilus-cd-burner and K3b, it's easy enough to master a CD -- just as easy as dragging files anywhere else.

If you would like to use the CD like a floppy, then **maybe you're better off with a USB stick**, or something else that is great for  countless read-writes![/QUOTE]
 I agree with you, I prefer not to use Packet Writing. I prefer to use iso9660, but in some new CD-RWs if I write it with k3b as a normal cd, I can't read it afterwards. Maybe I missed to do full blanking before using it for the first time as randy suggested?

Thanks lot

Rmdnet

---

