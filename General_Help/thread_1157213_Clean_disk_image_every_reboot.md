---
title: "Clean disk image every reboot?"
date: 2009-05-12
forum: General Help
---

### Post by seandiggity on 2009-05-12
Forgive my naiveté, but I'm having a lot of trouble finding information via a search engine or Wikipedia on this topic.

I have used machines in libraries and on loan from colleges that restore a fresh image of Windows XP every boot.  In some cases, I assume this is a network boot; nowadays it probably involves virtualization.

I know the classic way to solve this problem on Unix-like systems would be a read-only filesystem mounted from the network and the /home directories mounted from the local disk (or vice versa).

I would like to do the same thing with some machines in my office with Ubuntu and *without booting from the network*.  Instead I'd like to have the disk image on a small partition of the hard drive, and have that fresh image restored every boot.

Can I do this with an all-FOSS solution?  Is there one out there that would also allow me to restore fresh Windows images?  How would this effect GRUB and dual-boot machines?

Thanks in advance :)

---

