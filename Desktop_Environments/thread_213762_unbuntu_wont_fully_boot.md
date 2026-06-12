---
title: "unbuntu wont fully boot"
date: 2006-07-11
forum: Desktop Environments
---

### Post by osiris999 on 2006-07-11
so i got a new water cooling kit so i had to tear down my pc and re build it. now windows xp works fine but when i boot ubuntu it starts loading and stops of the 3rd thing (loading root file system i think it is) it just freezes and stays there. what could be wrong?

---

### Post by JohanSwe on 2006-07-11
Did you get rekommended to restart your computer after uppdating before quitting Ubuntu? I did and now my computer frezzes at 
> Mounting root file system..
Waiting for root file system..

---

### Post by osiris999 on 2006-07-11
no it started when i put my pc back together. ubuntu has never booted since. but that is where its hanging up at

---

### Post by DavidFL on 2006-07-11
> **osiris999 said:**
> so i got a new water cooling kit so i had to tear down my pc and re build it. now windows xp works fine but when i boot ubuntu it starts loading and stops of the 3rd thing (loading root file system i think it is) it just freezes and stays there. what could be wrong?

First thing is to use the Check CD for errors feature, then do the memory test.

---

### Post by JohanSwe on 2006-07-11
> **osiris999 said:**
> no it started when i put my pc back together. ubuntu has never booted since. but that is where its hanging up at
What I would like to now is not if you restarded the computer but if you got the question, because that would mean the your kernel has been updated, and that's when my computer started to freeze in the beginning of the boot precess, just like your computer.

---

### Post by Gus Tarballs on 2006-07-11
Did you change the hdd cables? Are the same drives still connected the same way/order as before? How about master and slave settings?
It sounds a bit like ubuntu/grub can find your /boot partition but not your /
Just a guess...

---

### Post by osiris999 on 2006-07-11
> **Gus Tarballs said:**
> Did you change the hdd cables? Are the same drives still connected the same way/order as before? How about master and slave settings?
It sounds a bit like ubuntu/grub can find your /boot partition but not your /
Just a guess...

i think that might be it

---

### Post by osiris999 on 2006-07-11
tried that and it worked. joahn i updated a long time ago with no problems. o pnly got this problem after putting my pc back together after installing the new parts for my water loop.

---

