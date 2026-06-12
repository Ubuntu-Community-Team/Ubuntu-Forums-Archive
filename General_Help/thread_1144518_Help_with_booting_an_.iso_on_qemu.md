---
title: "Help with booting an .iso on qemu"
date: 2009-04-30
forum: General Help
---

### Post by translucent juicebox on 2009-04-30
I'm trying to boot up a redhat install image in qemu directly from the drive but I keep getting the following error in qemu.

Boot failed:  not a bootable disk
FATAL:  no bootable drive

hears what I did in the terminal...

tyler@tyler-laptop:~$ qemu-img create -f qcow harddisk.img 3G
Formatting 'harddisk.img', fmt=qcow, size=3145728 kB
tyler@tyler-laptop:~$ qemu -cdrom /home/tyler/Desktop/7.0-i386-powertools.iso -hda harddisk.img
Could not open '/dev/kqemu' - QEMU acceleration layer not activated: Permission denied

I'm really confused and don't have much of a clue as to what I'm doing, what is wrong with how I'm asking qemu to boot?

---

### Post by translucent juicebox on 2009-05-01
Bump, I need help. :(

---

### Post by smoobandit on 2009-05-06
3 things:

1.  You may need kqemu.  Install as follows:

                                 ```
sudo apt-get install kqemu-common kqemu-source
```2. You need to run qemu with sudo.

3. qemu is trying to boot from the blank HDD image you make.  Use '-boot d' as an option for qemu to force it to boot from the cdrom.

---

