---
title: "Raid 0 Compatibility"
date: 2007-04-26
forum: Desktop Environments
---

### Post by RunningRabbit on 2007-04-26
Hello!

I am wondering if my Raid 0 configuration will work with Ubuntu. I am interested in switching, but I really want to be able to use my Raid setup. I don't have any floppy disk drivers (I don't even have a floppy drive in my computer), so I am not sure how I would go about installing the Raid unless it is natively supported (I believe it is a nForce raid chipset).

Any suggestions or information on this would be very helpful. Thank you!

---

### Post by ld50 on 2007-04-26
I just finished installing Edgy on Raid 0.  My chipset is the Intel ICH7 which could only be used as a software raid .  I initially tried to install Feisty but it simply would not boot.  The only trick is that I had to create a Raid 1 partition to mount as /boot so that the system could see it at startup it then sets up the other Raid 0 partitions (/, swap, /home).  So far so good, as soon as I hear of a successfull 7.10 setup I will be upgrading to that, may have to wait untill 7.10.  Good luck.

Also, I believe you may recieve more replies if this is in the Installation forum.

---

### Post by psusi on 2007-04-26
Take a look at [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

---

