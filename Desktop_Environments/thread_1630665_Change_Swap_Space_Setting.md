---
title: "Change Swap Space Setting"
date: 2010-11-25
forum: Desktop Environments
---

### Post by dontgetshocked on 2010-11-25
How can I add more space to my drive since I only have 1gb of ram and plenty of hard drive space? Right now it does not seem to be utilizing the swap space very efficiently.

---

### Post by 31632531 on 2010-11-25
[Swappiness]("http://www.n00bsonubuntu.net/ubuntu/swappiness")

---

### Post by dontgetshocked on 2010-11-25
Thanks

---

### Post by mcduck on 2010-11-25
> **dontgetshocked said:**
> How can I add more space to my drive since I only have 1gb of ram and plenty of hard drive space? Right now it does not seem to be utilizing the swap space very efficiently.

the thing is that you actually *don't* want to use swap, unless you really are running out of available RAM. Which shouldn't usually happen with 1GB of RAM.

Swapping doesn't improve performance, actually it decreases it. It's just a way for the operating system to do tasks that would require more than the amount of RAM available. But since swap uses hard drive to store the data, it's nowhere near the speed of using the RAM. Roughly thousand times slower. You'll definitely notice the lagging and general slowness of the system when it runs out of RAM and starts swapping...

(swap partition is also used for hibernating, which is pretty much the only situation when you'd actually *want* to use it for anything. So usually you'd define your swap size for this purpose only, and otherwise just do anything you possibly can to avoid swapping. :D)

---

### Post by dontgetshocked on 2010-11-25
Thanks for the education.I am planning adding another gig soon,I can only get 2GB of ram on my Asus EeePC 900 HD Netbook.

---

### Post by Enigmapond on 2010-11-25
Actually if you use that guide posted, put your swapness to 10...this is the recommended value but it will differ from system to system based on Ram size. I have 4GB of RAM and I NEVER even use the swap at this value...which is a good thing..:)

---

### Post by d3v1150m471c on 2010-11-25
I would suggest adding more ram. Yeah you can adjust the swappiness, of course, except that reading/writing from your swap partition is way slower than doing it on ram. Thus, you'll be able to run more at once but it won't make your computer any faster. If you prioritize the swap too high your machine will be slower.

---

### Post by mcduck on 2010-11-26
> **dontgetshocked said:**
> Thanks for the education.I am planning adding another gig soon,I can only get 2GB of ram on my Asus EeePC 900 HD Netbook.

I have only 1GB RAM on my desktop. :D And I do 3D graphics and video editing on it. And it never uses swap. ;)

I can't really even imagine how one might be able to use so much RAM on a netbook that swapping would be required... Or how one could actually make decent use of more than 1GB of RAM on a netbook in the first place... :o

---

### Post by dontgetshocked on 2010-11-26
Well, here is the answer! When it changes the wallpaper every little while it takes right at 90% of the cpu and stops you cold  what you are doing.Also I have read that if you have at least 2mb of ram then the os can perform better.You can never have too much ram.My solution lies in adding another mb of ram and disabling some services.Thanks,

---

### Post by mcduck on 2010-11-26
The wallpaper changing is about CPU usage, not RAM, so adding more RAM should not have any effect on that.

Also, it's very easy to have too much RAM installed. It happens the very moment you have more than the programs and tasks you do require, and more than the system can reasonably use as cache. After that adding more RAM is simple waste of money, it's going to sit there doing nothing at all. With current PC's shipping with 4GB of RAM, most people have a setup with more RAM than what they'll actually ever use (unless the use Windows on their machines, in which case I of course do understand the high amount of RAM :D)

Just run "free -m" in a terminal and check the amount of used swap. If it's 0 or something very small, you already have all the RAM you need. If the system is actively using the swap space, then you don't have enough RAM and should get more.

---

### Post by dontgetshocked on 2010-11-26
Thanks,I did not understand correctly.Since I dont think I can change the cpu,will have to take some load off the cpu.Hey its just a cheap netbook anyway,got it for 200.00.

---

