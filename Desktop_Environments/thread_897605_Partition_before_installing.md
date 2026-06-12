---
title: "Partition before installing"
date: 2008-08-22
forum: Desktop Environments
---

### Post by yosarian on 2008-08-22
I got a brand new computer and I want to install Ubuntu 8.04 but first I want to partition the hard drive in 2 (to have the personal data in D and the OS in C).
How can I do that?

---

### Post by snowpine on 2008-08-22
Hi Yosarian,

Here is a good intro to partitioning, read it carefully: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

It sounds like you want 3 partitions: / for the Ubuntu, /home for your personal data, and /swap (it's like virtual memory in Windows).

Ubuntu doesn't use the C:, D: naming system for drives like Windows does. :)

Once you've planned your partitions, you can create them by booting from the Live CD, going to the System menu, and choosing Partition Editor.

Good luck!

---

### Post by yosarian on 2008-08-22
thanks

---

### Post by tuxxy on 2008-08-22
bodhi wrote  good guide too

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by ajgreeny on 2008-08-22
Will you have windows as well, and if so which version?  If Vista, it is better to use the vista partition tool to shrink vista first, then use gparted to make the ubuntu partitions.  If you have XP, you can use gparted for the whole job without problem, just ensure you defrag windows a couple of times before you shrink the windows partition.

---

### Post by yosarian on 2008-08-22
> **ajgreeny said:**
> Will you have windows as well, and if so which version?  If Vista, it is better to use the vista partition tool to shrink vista first, then use gparted to make the ubuntu partitions.  If you have XP, you can use gparted for the whole job without problem, just ensure you defrag windows a couple of times before you shrink the windows partition.


It is a Ubuntu only computer.

I would like to use a program without having to use the live CD. It is anyway to do it?
Can I use fdisk from a floppy disk?

---

### Post by snowpine on 2008-08-22
> **yosarian said:**
> It is a Ubuntu only computer.

I would like to use a program without having to use the live CD. It is anyway to do it?
Can I use fdisk from a floppy disk?

I am not quite sure I understand your question. :)

If you don't want to go through a separate partitioning step, you can let the Ubuntu installer automatically partition the drive for you (choose 'guided partitioning--entire disk'). The only drawback to that is that it will not create a separate /home partition (which is optional anyway) unless you choose the manual option.

May I ask why you don't want to use a Live CD? You are going to be using the Live CD to install Ubuntu anyway, unless for some reason you can't boot from CD (which you did not mention in your original post). You are not going to be able to install Ubuntu from a floppy, so I am not sure what the point of partitioning from the floppy would be?

ps if you are talking about using Windows fdisk, it is not the right tool for the job! :)

---

### Post by sandysandy on 2008-08-22
> **yosarian said:**
> It is a Ubuntu only computer.

I would like to use a program without having to use the live CD. It is anyway to do it?
Can I use fdisk from a floppy disk?

for creating new partitions u can use gparted (burn as iso image on CD)

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

the gparted tutorial is here

[www.howtoforge.com/partitioning_with_gparted](www.howtoforge.com/partitioning_with_gparted)

regards

---

