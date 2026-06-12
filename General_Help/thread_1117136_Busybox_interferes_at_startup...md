---
title: "Busybox interferes at startup.."
date: 2009-04-05
forum: General Help
---

### Post by raedbenz on 2009-04-05
hi,,

i have installed busybox on ubuntu8.04 but i didnt used it.
i have removed the gdm at startup: ```
sudo update-rc.d -f gdm remove
```

after i restart the PC it boots in busybox with "(initramfs)" in the begging of the line, and i only have limited commands. and i cant do anything.how to get rid of busybox?
how to get things back to normal??

thanx

---

### Post by gamewolf on 2009-04-05
I would try to boot into recovery mode from the Grub menu.
If that doesn't work, put in the Ubuntu CD and boot the LiveCD.
Mount your partition and chroot into your partition mount.
Then uninstall busybox.

If there's trouble post back.

---

### Post by raedbenz on 2009-04-06
hi,,
here is what i have done:

1- booted from the CD.
2- in the terminal i typed:```
sudo mount /dev/sda1 /mnt
```
3- cd to /mnt
4- ```
sudo apt-get remove busybox
```
but still doesnt work..

---

### Post by raedbenz on 2009-04-07
The busybox-initramfs when i try to uninstall it, it says that "NetworkManager applet could get all resources, and uninstallation is not complete".
after that i rebooted the PC and i lost the Kernel Version in Grub menu. only memtest86+ is available.
hints?

---

