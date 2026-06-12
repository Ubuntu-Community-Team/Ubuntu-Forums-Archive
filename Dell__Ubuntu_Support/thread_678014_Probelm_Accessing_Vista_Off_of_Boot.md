---
title: "Probelm Accessing Vista Off of Boot"
date: 2008-01-25
forum: Dell  Ubuntu Support
---

### Post by gecko113 on 2008-01-25
Hey everyone, I have a problem with Linux (Ubuntu 7.10) i installed it on to my external harddrive and now once i boot up i get a grub error 5 but i used Gparted to reformat my external but i still can not acces my on harddrive on my laptop

---

### Post by jeffus_il on 2008-01-25
Ubuntu has been erased, but grub is still being booted into, Use SuperGrubDisk.
Or use the liveCd to run grub-install to update grub to pick up your windows installation.

---

### Post by gecko113 on 2008-01-25
Where would i be able to find that i'm new to the whole Ubuntu OS

---

### Post by gecko113 on 2008-01-25
Under wat option on the live Cd do i use?

---

### Post by jeffus_il on 2008-01-25
I think you easiest solution may be to download the supergrubdisk iso (cd image) burn it, and boot from it to fix you boot.

---

### Post by gecko113 on 2008-01-25
Alrite well i went through the terminal and went through the setup
sudo grub
grub> find/boot/grub/stage1 after i input that i get another error 27: Unrecognized command

---

