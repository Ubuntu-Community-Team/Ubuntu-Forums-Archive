---
title: "Dell Studio &amp; Grub conflict"
date: 2010-11-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by putz3000 on 2010-11-21
My dad wanted to dual boot his Dell Studio between Vista and Ubuntu 10.04.  I do this all the time with my dell laptop so I did not think there would be a problem...but I was wrong.

I first shrunk the main Vista partition using Vista.  Then from the install disk I told Ubuntu to use all free space.  My first clue that something was wrong was the import question during install.  Ubuntu wanted to import from the "Windows Recovery Environment".  At the time I just figured it was a naming thing and continued with the install.  

After install I discovered that it really is the Windows Recovery Environment that Grub / Ubuntu sees.  Since every change to Grub causes a new scan of the system, every manual change I make gets over written.  I even installed "startup-manager" but it only sees the recovery partition.

Basically the problem is Grub only sees and wants to boot Windows from the sda3 partition (hd0,3) but the real windows partition that we need to boot from is sda2 (hd0,2).

My dad is new to Linux and new to Ubuntu.  Although it could be a great learning exercise to constantly have to manually edit Grub, it would be a pain and would get old pretty fast.  Has anyone experienced this and is there any way to fix this short of getting rid of Windows all together?

---

