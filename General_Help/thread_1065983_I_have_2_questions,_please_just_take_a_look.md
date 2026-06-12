---
title: "I have 2 questions, please just take a look"
date: 2009-02-10
forum: General Help
---

### Post by Til_Valhall_vi_drar! on 2009-02-10
allright, first one:

i have been sufering for a long time getting wake on lan to work, now, i took and hibernated my computer instead of shutdown from the menu and the halt, poweroff commands. wake on lan works only when i hibernates, and hibernating isn't something i like for some reasons, so if anyone could give me a hint on how to get the halt and poweroff commands do the same thing it would be great.

second question: i want to make my own initrd, just for fun. i have done some reverse engineering and i have figured out that the initrds are gzipped then some way zipped with cpio if you know what i mean, well i found some files in the initrd and the main script. so first of all, i want to start with just getting the bootloader to load the kernel and then an initrd which just executes /bin/sh. btw im experimenting this on a diskless computer with netboot. so if anyone could tell men what the requirements for this to work it would have been great, and sorry for my poor english.

and when im on it, here is a third question, is it busybox the initrd is using? can busybox be used in initrd?

i don't just want to use mkinitrd or something like that, i want to create it from bottom.

again sorry for my bad english and my stupid questions.

---

### Post by Til_Valhall_vi_drar! on 2009-02-10
hamburger

---

### Post by cariboo on 2009-02-10
I don't know about your wake-on-lan problem, I just leave my server on all the time, and it is connected to a ups.

Have you had a look at this [initrd howto]("http://www.linux-boot.net/InitRD/Howto/")?

Jim

---

### Post by Til_Valhall_vi_drar! on 2009-02-10
i shall look at it now, my wake on lan computer is not my server, my server is of course online 24/7, i want to use wakeonlan to get my server to wake up my computer with surround sound at the morning so i'll have atleast a chance to get up xD

lovely howto, but to tired now, going to take it in the morning. thanks^128

---

