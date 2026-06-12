---
title: "Triple boot: Vista, Ubuntu, Dell Mediadirect on Inspiron E1705"
date: 2007-07-06
forum: Dell  Ubuntu Support
---

### Post by coldfusion245 on 2007-07-06
Hello,

I've had some similar issues to what I've seen in these Dell forums - after installing Linux on my computer that originally had Vista and MediaDirect, MediaDirect would stop working. 

I'd like to know how to get a "triple" boot - with Vista, Linux and MediaDirect all functioning. Currently, only Vista and Linux work - MediaDirect cannot boot. If anyone has any suggestions, thoughts, or questions please tell me. I would greatly appreciate any advice that can help me get this to work. 

My computer: 64-bit Core 2 Duo Processor, 80GB SATA hard drive

My hard drive is using GRUB to boot. From /bin/grub/menu.lst, I found the following items:
Ubuntu linux (hd0, 3)
Windows Vista (hd0, 1)
Windows Vista Extended (hd0, 4) *This item won't boot from GRUB

Using Disk Manager in Windows, I found 5 partitions on my disk
hd0, 0 - 47 MB - EISA configuration (can someone tell me what this is?)
hd0, 1 - 64 GB - Primary partition for Windows
hd0, 2 - 8 GB - Primary partition for Linux filesystem
hd0, 3 - 430 MB - Primary partition for Linux swap
hd0, 4 - 2 GB - Primary partition for (*I think) MediaDirect

When I push the MediaDirect button, it starts booting up (at least I think it does), but generates an error that says something like
"Plug and play found an incompatible driver on your system..."
Technical information
STOP 0x000000CA (0x00000001, 0x83B624D8, 0x83B6B6A0, 0x00000000)

I'm guessing that MediaDirect doesn't like GRUB. I've read in the other threads that you have to use the Vista boot loader and add Linux into that, but I'm not sure how. If anyone can walk me through that I would greatly appreciate it. 

My email: [email]coldfusion245@gmail.com[/email]

---

### Post by ridgeland on 2007-07-06
I've never seen Vista or MediaDirect
but the hd0,0 = 47MB partition on my PC is DellDiagnostics.
I wouldn't change it as it has some simple tools that may help in trouble shooting some day.

Good luck with the rest.
( I don't stop at triple boot, I usually have 5 to 10 Linux OS partitions on my PC and test new Linux distros/releases for fun)

---

