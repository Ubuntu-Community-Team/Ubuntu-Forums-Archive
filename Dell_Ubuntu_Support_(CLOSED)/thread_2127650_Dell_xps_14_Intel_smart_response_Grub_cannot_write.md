---
title: "Dell xps 14 Intel smart response: Grub cannot write bootloader"
date: 2013-03-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by AndrosCr on 2013-03-20
I have a Dell xps 14 with dualboot windows 7 / ubuntu 12.10

on the windows side is active intel smart response ssd caching, while on the ubuntu side 11Gb ssd space is accessible as /dev/sdb1 .
windows and ubuntu are installed in /dev/sda, while /dev/sdb is dedicated to caching and for bootloading.

Now the nasty part: while caching is active, windows can modify /dev/sdb's mbr, while ubuntu cannot. funny thing is, no errors are reported by grub while doing a grub-install.

Right now the only solution i found is to deactivate caching from windows, do my business on the mbr from ubuntu, and reactivate caching on the windows side.

also, while this setup worked for the last couple of weeks, suddenly linux is unable to find the root partition by uuid, because it sees all the uuid as 00000000-0000-0000-0000-000000000000

i suspect that these problems are somewhat related, but i don't know where to start looking. So, any help is greatly appreciated!

additional info
   kernel: 3.7.0-7-generic
   dm-raid: i'm not sure what is the purpose and how it works :P

---

