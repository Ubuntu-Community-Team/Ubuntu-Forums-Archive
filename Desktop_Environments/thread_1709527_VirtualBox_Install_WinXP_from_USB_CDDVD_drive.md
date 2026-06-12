---
title: "VirtualBox: Install WinXP from USB CD/DVD drive"
date: 2011-03-18
forum: Desktop Environments
---

### Post by treacl on 2011-03-18
Hello everyone,

I am trying to install Windows XP on VirtualBox, using an external USB CD/DVD drive. VirtualBox boots to the CD/DVD and goes through the first part of the installation flawlessly. After XP restarts from the HD, however, it can't complete the installation because it can't find the files at "D:\I386\asms". (In fact, it doesn't seem to be able to access the CD/DVD drive at all.) I'm just guessing, but could this be because of how VirtualBox handles USB drives and/or because (if I recall) XP lacks native support for USB? Any suggestions?

Hardware and software specs:
--Lenovo ThinkPad X201
--Asus SDRW-08D1S-U external USB CD/DVD drive
--Ubuntu 10.04.1 64-bit (kernel 2.6.32-30)
--VirtualBox 4.0.4 (from [http://download.virtualbox.org](http://download.virtualbox.org))
--WinXP SP2 32-bit (original, retail install disc)

Many thanks,
treacl

P.S. I Googled around a lot about this. There are plenty of threads about how the open-source version of VB doesn't support USB, but nothing about installing from a USB source as far as I could find.

---

### Post by MartyBuntu on 2011-03-18
Why not try copying the contents of the XP disk to a folder and then point Virtualbox to the folder as an installation source? Worth a try.

---

### Post by treacl on 2011-03-18
I thought about doing something like that, but it seems to be XP, not VirtualBox, that has trouble accessing the optical drive. So if I copied installation files from the XP CD to a folder on the Ubuntu HD, I would need to map that folder to an XP drive letter--and I would need that mapping to be in place *before* XP was fully installed. Any idea how to do that?

---

### Post by treacl on 2011-03-19
Here's the answer:

[http://forums.virtualbox.org/viewtopic.php?f=2&t=40048](http://forums.virtualbox.org/viewtopic.php?f=2&t=40048)

---

