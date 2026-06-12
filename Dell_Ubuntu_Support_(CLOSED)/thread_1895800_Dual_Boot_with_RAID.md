---
title: "Dual Boot with RAID"
date: 2011-12-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lile001 on 2011-12-15
Iam thinking about purchasing a Dell, then configuring it as follows:

THe box will have maybe a 250GB hard drive from the factory, with Windows installed on it.  I will purchase separately a hardware RAID controller and two additional hard drives, maybe 250GB each. I'd like to have dual windows/ubuntu boot. The RAID will be my Ubuntu partition, which is also where all my important business files will reside.  The WIndows partition allows me to run some software that won't run under WINE, other than that it won't get used.  

How to proceed?  SHould I get the box from Dell, install the RAID hardware, then install Ubuntu? Or would it be better to install the RAID hardware after Ubuntu is installed?  

There is some sticky information at the top of this forum about DELL having an "ISO" for Ubuntu (whatever that is) , but it swiftly degrades into technical gibberish that I don't understand.  Is this something that will be useful for a dual boot installation like this? I don't really know what any of that means. 

P.S. - I tried FakeRAID software raid and was unable to make it work.  Hardware RAID is what I need.  I have been pretty happy with Dell (others have complained otherwise!) so I will buy another one.

---

### Post by Blinkiz on 2011-12-17
If you are using true hardware raid, Ubuntu will just see your two new hard drives as one.
You install your RAID card first and then install Ubuntu.

I will not get into a debate why you getting real hardware raid, so I skip that talk. Let me know if you want to discuss this. :)

---

