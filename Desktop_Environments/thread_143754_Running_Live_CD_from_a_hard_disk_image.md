---
title: "Running Live CD from a hard disk image"
date: 2006-03-13
forum: Desktop Environments
---

### Post by unisis on 2006-03-13
Dear all,

Is there a way to run UBUNTU 5.10 Live CD in a image file copied to the Hard Disk  ?
I mean not installing, just copying the image to the HDD & booting from there as follows.

For an example :-
	we can run knoppix with the image on the hard disk. Knoppix CD needs not to be in the CD rom all the time to run knoppix under this method.

knoppix tohd=/dev/had1 (To copy the iso image to the HDD)
knoppix fromhd         (Boot knoppix from the HDD)


Can UBUNTU be run in the above manner ? What is the method ?


I will be pleased if someone could answer my question.

Thanks ! 
:-D

---

### Post by muzaki on 2006-03-13
if i got u correct u want to run / emulate os from inside os?

then try qemu ...
i used to use qemu to do this.

[http://fabrice.bellard.free.fr/qemu/download.html](http://fabrice.bellard.free.fr/qemu/download.html)

> QEMU is a generic and open source processor emulator which achieves a good emulation speed by using dynamic translation.
QEMU has two operating modes:

    * Full system emulation. In this mode, QEMU emulates a full system (for example a PC), including a processor and various peripherials. It can be used to launch different Operating Systems without rebooting the PC or to debug system code.
    * User mode emulation (Linux host only). In this mode, QEMU can launch Linux processes compiled for one CPU on another CPU. 

---

### Post by yusufk on 2006-03-13
I think that you can mount the .iso file using a loop mount. Not sure exactly how to do it, but I'm sure that u'll find something if u search the forum for loop mount.

---

