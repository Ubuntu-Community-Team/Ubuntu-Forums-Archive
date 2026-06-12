---
title: "Installing 7.10 on a 9200 - disk problem."
date: 2008-01-07
forum: Dell  Ubuntu Support
---

### Post by gonesolo on 2008-01-07
I bought a 9200 a while ago and I have Vista installed (just for games trust me)

Any way I want to install Ubuntu 7.10 in a dual boot but here is my problem.

I have two 320GB hard disks and due to a Vista problem with SATA controllers I have my SATA controller in RAID mode and I have a single 640GB RAID 0 across both my hard disks. I have Vista installed in a 400GB partition and I want to install Ubuntu in the spare 200GB.

My problem is when I start the Ubuntu installation it only sees the two seperate hard disks and not the single RAID 0. If I change my controller back to SATA mode there is a possibilty I will loose connection to my CD/DVD drives in Vista.

Is there anyway Ubuntu will see the RAID 0 or am I SOOL????:confused:


Update: OK after a little research I think I've found the solution. I need to use DMRAID to see the SATA RAID 0 as I have Vista already install and the LIVE CD install of Ubuntu doesn't work on my system (due to the 8800GTX video card) I think I'll have to delete my RAID 0 (and my current OS) and re-create the two seperate drives.

---

