---
title: "Inspiron 9400(/ e1705) 4gb ram DOESN'T WORK!"
date: 2008-01-14
forum: Dell  Ubuntu Support
---

### Post by exoren22 on 2008-01-14
So I set up a Gutsy 64bit/Vista dual boot that I am particularly proud of (I love Vista AND Ubuntu, so don't complain about either). Anyway, I decided to upgrade from 2gb to 4, and after I installed the two chips I ran the dell setup utility, which recognized the 4 gigs. The dell BIOS saw all 4 gigs, but due to the lack of memory hole remapping(c'mon, Dell, wtf?!) it only uses 3.25gb. I am fine with this, as its 1.25gb more than I had previously.

 So, I booted Vista and I was very impressed by the performance increase (Vista's designed for memory consumption), but Ubuntu just freezes on boot. I select it from the boot menu and the boot splash starts, but when the gdm starts its so excruciatingly slow I have to let it sit for 20 minutes while it loads. Then I log on, and the desktop (Xubuntu with compiz) partially loads after 30 minutes and it just refuses to do anything. I even let it load overnight, but nothing. Ctrl+ALt+Backspace does kill X, and the restart takes as long as before.

When I load recovery mode it takes noticeably longer than before, but it does load, and when I run Top it recognizes 3.25gb. As a final slap in the face, no Ubuntu LiveCD will boot. I select any boot option and it just sits there with the X cursor flashing. I can kill the x environment, but no shell will load. 

Honestly, I have no idea what to do at all. Why will Vista work sooo well, but Ubuntu refuse to boot?

AAAAAAAAAAAAAAAAAAAAAARRRRRRRRRRRRRGGG!
Sorry, I needed that.

---

### Post by jerrylin on 2008-01-15
This sounds like a particularly strange situation. Are you 100% sure your CPU is a 64-bit chip?

If Vista is not the 64-bit version that would explain the 3.25gb of visible RAM which is to be expected with a 32-bit OS.

---

### Post by m94mni on 2008-01-15
You'll *never* get more than 3.25Gb on this machine. The issue is not the processor or the OS but the 32-bit PCI hardware. There simply is no way to use the top memory as that section of the address space is needed by the PCI hardware.

Sorry, but you need a Santa Rosa laptop (inspiron 1720) to use 4Gb.

---

### Post by exoren22 on 2008-01-15
Just to let both of you know, my 1705 is a Napa machine with a core 2 duo (actually a centrino duo), but I don't care about the lack of .75gb, i want the use of linux. I am using 64-bit vista and linux. Linux worked perfectly before I upgraded the memory, and now it doesn't. Vista still works. Gentoo said it could not initialise an x session. So, I booted up the recovery console and ran a dpkg-reconfigure xserver-xorg, which detected no graphics card. I believe this is the root of the problem. 

Also, I switched back down to 3gb and linux works perfectly. I am considering getting a new motherboard to try to fix the 4gb limit, but I want to be absolutely certain I can use my graphics card. 

Oh well. Hopefully someone has a more concrete answer.

---

### Post by m94mni on 2008-01-16
You either have a hardware problem that doesn't manifest itself in Vista or your ubuntu installation is somehow corrupt.

I run Ubuntu (32bit on a T2600) with 4Gb RAM with no issues on my M1710.

Have you tried another LiveCD? Feisty, or another distribution entirely? A 32 bit version?

---

### Post by exoren22 on 2008-01-16
I've tried the KDE 4.0  liveCD from kubuntu (which is i386), and i tried gentoo liveDVD (i have a really fast ethernet connection, :] ). It's not a hardware issue, although it may be a bios issue, but I did fing one time that someone running fedora on a similar system had to install a kernel extension to be able to read the graphics card that's mapped into the 4gb memory space. I couldn't find it again, however. 

If it helps, i'm writing this on my machine in ubuntu 7.10 after swapping one of the 2gb chips for a 1gb chip.

---

