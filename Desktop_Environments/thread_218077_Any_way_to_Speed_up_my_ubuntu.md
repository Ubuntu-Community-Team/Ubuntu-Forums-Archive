---
title: "Any way to Speed up my ubuntu???"
date: 2006-07-18
forum: Desktop Environments
---

### Post by morbid_bean on 2006-07-18
I have a somewhat crappy computer 500mhz 128 mb of ram...any ways i am currently still using ubuntu 5.10 because version 6.06 is to powerful for my system. But my question is,  Is there a way to speed up my ubuntu...ive changed my theme to the simple...that helps a little bit...is there any other settings I could change to boost it, when i try to open office word, it literaly takes like 3 mins. and i know that isnt normal....so if there is any other thing i could change to help this system out...(LOL ITS EATING ALL MY MEMORY!!!) please please!! tell me what it dose and how to do it.  ](*,)  ](*,)  ](*,)

---

### Post by JerMe on 2006-07-18
[http://ubuntuforums.org/showthread.php?t=189192](http://ubuntuforums.org/showthread.php?t=189192)

---

### Post by swamytk on 2006-07-18
1. Disable all unnecessary services in /etc/init.d directory. I use to create a backup directory in /etc/init.d and move unnecessary services scripts file to backup directory.
2. Add swap space of atleast 512MB.
3. If you have internet, go for update with XFCE or other lighter desktops.

---

### Post by asplode on 2006-07-18
You also might want to consider checking out the Dapper release of [Xubuntu]("http://www.xubuntu.org/"), a release specifically tailored with XFCE desktop environment in mind. That way you won't have to deal with GDM, (at least I don't believe so) which should also improve the boot time of an older computer, and have the benefits of all the hard work and fixes the developers put into Dapper, without the overhead of GNOME.

---

### Post by morbid_bean on 2006-07-19
> **asplode said:**
> You also might want to consider checking out the Dapper release of [Xubuntu]("http://www.xubuntu.org/"), a release specifically tailored with XFCE desktop environment in mind. That way you won't have to deal with GDM, (at least I don't believe so) which should also improve the boot time of an older computer, and have the benefits of all the hard work and fixes the developers put into Dapper, without the overhead of GNOME.

So what is diffrent from the ubuntu i have and the xubuntu?...this ubuntu is the first linux i was  actually happy with....is xubuntu about the same or are there big changes?  Im wondering if i will be able to operate is as easy as i do with the one i have now.

---

### Post by aysiu on 2006-07-19
Xubuntu is just a lighter desktop environment. Try it out: ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
``` Log out and from the menu select the session **XFCE** instead of **Gnome**. Then log back in again.

---

