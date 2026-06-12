---
title: "no sound in xubuntu dapper"
date: 2006-06-02
forum: Desktop Environments
---

### Post by bionnaki on 2006-06-02
I just installed xubuntu dapper on my friend's computer. I previously had xfce via breezy server install and the sound worked out of the box. For some reason unkown to me, there is no sound with xubuntu. 

He has onboard sound - no soundcard.

Any ideas?

hmmm

---

### Post by jazzgossen on 2006-06-02
Try running gnome-alsamixer and play with the settings there to see if any sound comes out. I had to change some stuff there after the last Ubuntu Dapper update.

---

### Post by UncleOwl on 2006-06-02
The problem might be that you are still running the Breezy kernel (happened to me). Somehow GRUB refused to register the new 2.6.15 kernel and only gave me the option to run the old 2.6.12 which lost sound when coming up (the machine is Thinkpad T43 laptop). The solution I found was to edit the /boot/grub/menu.lst and describe the new kernel manually - find the section with something like this:

title Ubuntu, kernel 2.6.12-10-386
root (hd0,2)
kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/sda3 ro quiet splash
initrd /boot/initrd.img-2.6.12-10-386
savedefault
boot

copy it before itself and modify the version numbers to be 2.6.15-23 , remove the "savedefault" from the old location.  Save and restart.

Worked for me, the new kernel came up and sound is now as good as it was in Breezy.

---

