---
title: "Ubuntu isn't starting. :/"
date: 2005-09-11
forum: Desktop Environments
---

### Post by Chaykin on 2005-09-11
Yesterday I worked normally on my Ubuntu. Then I saw a update menager icon that there are some updates. There was a new version of "libssl" and "linux-image" (or sth like that, I don't remeber the names exactly). Ok - so I started the update process. It worked fine. I was still working normally... I switched off the system and went sleep. Today I'm turning on my computer and Ubuntu doesn't start. :/ Here is the log:
```
root (hd0,2)
 Filesystem type is ext2fs, partition type 0x83
kernel  /boot/vmlinuz-2.6.10-5-386 root=/dev/hda3 ro quiet splash
   [Linux-bzImage, setup=0x1600, size=0x120adh]
initrd  /boot/initrd.img-2.6.10-5-386
   [Linux-initrid @ 0xfbad000, 0x433000 bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
```
And then the computer freezes. :[ It doesn't react on anything. The situation is the same with recovery mode. Any ideas? Please, I'm begging for your help. :( (And I hope you understand my 'engrish')

---

### Post by lompolo on 2005-09-11
Can you test older image. Just like you test the recovery mode. Esc from grub starting and choose image lower number than highest. If this works you can remove newer image from synaptic.

---

### Post by Chaykin on 2005-09-11
I accessed my linux partition booting the Ubuntu from LiveCD and mounting the partition. In /boot folder I have only this files: ```
config-2.6.10-5-386
initrd.img-2.6.10-5-386
memtest86+.bin
System.map-2.6.10-5-386
vmlinuz-2.6.10-5-386
```And grub folder. I don't have any idea what to do. :( Please help! :/ Your advice lompolo isn't working. :(

---

### Post by cwaldbieser on 2005-09-11
Would it be possible to boot using the LiveCD, mount the Ubuntu hard drive, chroot to it, then apt-get an older linux-image?

---

### Post by krokodil on 2005-09-19
I have had this exact same problem. Twice. But on another machine I have no problems. I managed to roll back linux-image using a Ubuntu LiveCD.

I have no idea what the problem is. How can I update linux-image without any problem?

---

