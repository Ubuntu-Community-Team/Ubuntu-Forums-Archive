---
title: "Occasional freezing"
date: 2009-04-12
forum: General Help
---

### Post by peterqb on 2009-04-12
My machine freezes occasionally, which means that watching a DVD is out of the question, but otherwise it works fine with apps, including Skype.

My specs are:

Ubuntu 8.10
Linux 2.6.27-11-generic
GNOME 2.24.1

RAM: 438.4 MB
CPU:  AMD Sempron 2800+
Disk:100 GB free


Is the machine just too slow, or is there anything I could do to make it smoother for video tasks?
--
pqb

---

### Post by lovinglinux on 2009-04-12
This might help you [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by zigga15 on 2009-04-12
There are many reasons why this could be happening.

Assuming this happens when you are watching a DVD, It could be something to do with your actual drive.

You do have an older machine, so try reducing your resolution before watching a DVD.

You could also increase/decrease the size of the buffer on your player.

> **peterqb said:**
> My machine freezes occasionally, which means that watching a DVD is out of the question, but otherwise it works fine with apps, including Skype.

My specs are:

Ubuntu 8.10
Linux 2.6.27-11-generic
GNOME 2.24.1

RAM: 438.4 MB
CPU:  AMD Sempron 2800+
Disk:100 GB free


Is the machine just too slow, or is there anything I could do to make it smoother for video tasks?
--
pqb

---

### Post by peterqb on 2009-04-12
Thanks very much. That seems to have helped a bit. The picture is smoother.

It is not just with movies though. The computer freezes for a few seconds from time to time and I wondered if there are configs I can change, allocating more memory to video for example.

Many thanks.
--
pqb

---

### Post by DeMus on 2009-04-12
> **peterqb said:**
> Thanks very much. That seems to have helped a bit. The picture is smoother.

It is not just with movies though. The computer freezes for a few seconds from time to time and I wondered if there are configs I can change, allocating more memory to video for example.

Many thanks.
--
pqb

It could be the amount of RAM memory, which is a little low. I'm not saying it is too low, but when you use System monitor and look at the amount of memory being used you probably see it is almost 100%. Then Swap kicks in, which makes the computer slower. It could be when parts of the memory are being transferred to swap (or vice versa) the computer is so busy it doesn't have time for your programs.
Is there a way to get more memory in your computer? It would most certainly help you out.

---

### Post by peterqb on 2009-04-14
> **DeMus said:**
> It could be the amount of RAM memory, which is a little low. I'm not saying it is too low, but when you use System monitor and look at the amount of memory being used you probably see it is almost 100%. Then Swap kicks in, which makes the computer slower. It could be when parts of the memory are being transferred to swap (or vice versa) the computer is so busy it doesn't have time for your programs.
Is there a way to get more memory in your computer? It would most certainly help you out.

Yes, I think it is probably that. Thanks for the tip. I've been looking at minimum specs for watching DVDs, and the processor speed looks fine, but I may need to update graphics card drivers. I'll post again if that makes a difference, otherwise it's down to the local store for more RAM :-)

---

