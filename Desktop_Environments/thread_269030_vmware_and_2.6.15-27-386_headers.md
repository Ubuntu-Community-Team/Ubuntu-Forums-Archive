---
title: "vmware and 2.6.15-27-386 headers"
date: 2006-10-01
forum: Desktop Environments
---

### Post by dpsleep on 2006-10-01
so im trying to install vmware and during the config it wants to compile a new vmmon. i went and got [linux-headers-2.6.15-27-386]("https://launchpad.net/distros/ubuntu/dapper/i386/linux-headers-2.6.15-27-386/2.6.15-27.48")
but when i tell it where the right headers are it gives me
```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.15-27/include

The directory of kernel headers (version 2.6.15-27) does not match your running
kernel (version 2.6.15-27-386).  Even if the module were to compile 
successfully, it would not load into the running kernel.
```
does anyone know what i need to do here?
dpsleep

---

### Post by dpsleep on 2006-10-01
bump...

---

### Post by ArponerO on 2006-10-01
Hi,

Try vmware-any-any-update104. This is a vmware patch for new kernel versions. 
Hope this helps.

---

### Post by dpsleep on 2006-10-01
already tryed that and it didnt really make a difference. thanks for helping though...

---

### Post by Bunto0 on 2006-10-03
its simple. i'm actually doing the same thing right now. when you installed the linux headers there is two directories. the one that you gave it and another one that is exactly the same except with the -386 on the end.

SO!

what you need to type is:

/usr/src/linux-headers-2.6.15-27-386/include

that should work.

let me know.

---

