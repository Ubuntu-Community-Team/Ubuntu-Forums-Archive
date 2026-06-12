---
title: "Ubuntu Crashes Constantly"
date: 2007-06-22
forum: Dell  Ubuntu Support
---

### Post by anotherpunk on 2007-06-22
I'm running Feisty on my Dell Latitude laptop and it usually hangs or crashes while running Update Manager and even sometimes while in Firefox.


Can anyone help me out?

edit: A little while back, after restarting Ubuntu, GRUB listed Ubuntu and the recovery partition twice. I'm curious why.

---

### Post by chippy99 on 2007-06-22
Just an idea but Linux crashes are frequently cause by problems with faulty memory. Try running MemTest, it should be an option from the grub menu. If not you will have to install it

---

### Post by vexorian on 2007-06-23
> **anotherpunk said:**
> I'm running Feisty on my Dell Latitude laptop and it usually hangs or crashes while running Update Manager and even sometimes while in Firefox.


Can anyone help me out?

edit: A little while back, after restarting Ubuntu, GRUB listed Ubuntu and the recovery partition twice. I'm curious why.
You probably did an upgrade, when the kernel is updated, the old version is kept in grub, just in Case the new kernel doesn't work CorreCtly for you, you might remove it manually from /boot/grub/menu.lst if you have the expertize to edit that file and onCe you know the new kernel version works CorreCtly for you.

---

### Post by anotherpunk on 2007-06-23
> **chippy99 said:**
> Just an idea but Linux crashes are frequently cause by problems with faulty memory. Try running MemTest, it should be an option from the grub menu. If not you will have to install it

What should I look for when I run MemTest? I remember running it before and it going on forever.

---

### Post by fjgaude on 2007-06-23
> **anotherpunk said:**
> What should I look for when I run MemTest? I remember running it before and it going on forever.

It will report any bad cells... just let it run until it is finished with all the tests... does take a long time.

frank

---

### Post by Tethtibis on 2007-06-26
plus, there are alot of times, memory won't show up bad untill it gets warm. about 125 degrees Fahrenheit. with desktops, it's common to run the mem test while using a hair dryer pointed at the memory, but with laptops, just have it cycle the memtest and go watch a movie or something. it has to heat up a bit.

---

