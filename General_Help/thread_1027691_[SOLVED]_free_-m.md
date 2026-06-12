---
title: "[SOLVED] free -m"
date: 2009-01-01
forum: General Help
---

### Post by xoorath on 2009-01-01
hey all, I have 4gb of ram and am using ubuntu 32bit; I know I am only able to see ~3.5gb of my ram; however I noticed that when I installed ubuntu, I made a 1gb swap partition, but when I use free -m it tells me I'm not using any of my swap memory. I was wondering if ubuntu is unable to use the swap partition I made for it, or if I have so much ram, it doesn't need to use the swap. If its because I have more memory then necessary, then is there a way to get rid of my swap partition to give that 1gb back to me? perhaps put it onto my storage partition? here's some info:

free -m:
> 
xoorath@2xoor-desktop:~$ free -m
-------------total-------used-------free-----shared----buffers-----cached
Mem:-----3545--------907-------2637----------0---------34-----------505
-/+ buffers/cache:        367------3178
Swap:-----980----------0---------980

my configuration as of now:
 
> 500GB hard drive:
50GB partition - Windows XP 32 bit (ntfs)
50GB partition - Windows Vista 64 bit (ntfs)
50Gb partition - Ubuntu 32 bit (ext3)
1Gb partition - Swap (swap)
[the rest] - Storage (ntfs)

4Gb of ram (2x2gb)

---

### Post by drs305 on 2009-01-01
Your swap is enabled but not currently needed. If it were not enabled or there was a problem you would get zeros with the "free -m" command.

Your swap partition size seems reasonable. Even if not using it at the moment it could be called upon - including if you choose to suspend your system. Some recommend having a swap equal to your memory, but if you aren't having problems I wouldn't change it. Reducing the swap partition would not be worth it for such a small gain in disk space IMO.

---

### Post by damis648 on 2009-01-01
32-Bit operating systems cannot handle more than 4GB of memory, including video memory, that reserved for the kernel, etc. so for you comes out to 3.5GB. In order  to use more than 4GB of RAM, you can either:
1. Install the server kernel, which is compiled with PAE so that >4GB RAM can be used in a 32-Bit OS.
2. Install 64-bit Ubuntu.
or
3. Compile your own kernel with support for 64GB RAM (PAE), but this is an advanced task.

---

### Post by xoorath on 2009-01-01
I recently got this copy of ubuntu in the mail; I dont even remember ordering it, but I thought "how odd... oh well, lets try something fun and geeky; how about tri booting..." so here I am. I dont intend on getting 64bit ubuntu, but I would love to try compiling my own kernel some time, but not for tonight. I think I will take the advice of keeping my 1gb swap. I will be creating a new thread shortly for another matter I need assistance with; so anyone who can, or wishes to do so, may consider this solved.

---

### Post by drs305 on 2009-01-01
> **xoorath said:**
> I will be creating a new thread shortly for another matter I need assistance with; so anyone who can, or wishes to do so, may consider this solved.

Only the original poster (you) or the mods (who won't) can mark the thread solved. You can mark it solved with the Thread Tools link to the upper right of the original post. You can also return there to mark it 'unsolved' should the need arise.

Good luck resolving your other problem.

---

### Post by xoorath on 2009-01-01
neat; thanks for that.

---

