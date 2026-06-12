---
title: "Encrypted file system, AES EFT"
date: 2006-11-11
forum: Desktop Environments
---

### Post by mistermax on 2006-11-11
I've been trying to follow Hack#70 from the Ubuntu Hacks book, trying to set up my /home as an encrypted device using dm-crypt.

I've loaded up aes using modprobe-

sudo modprobe aes

I've then installed cryptsetup-

sudo apt-get install dmsetup cryptsetup

but when I check to see that the dmsetup package has created the device manager-
ls -l /dev/mapper/control 

I'm informed that there is no such file or directory...

What do I need to complete the AES setup, encrypting home on my harddrive?

---

