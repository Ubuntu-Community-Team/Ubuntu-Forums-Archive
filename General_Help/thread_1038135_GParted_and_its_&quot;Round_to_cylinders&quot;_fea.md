---
title: "GParted and its &quot;Round to cylinders&quot; feature"
date: 2009-01-12
forum: General Help
---

### Post by Zacaretas on 2009-01-12
Hello!

I popped in my 8.10 Intrepid Ibex Live CD a few moments ago and started to use GParted 0.3.8 to partition my hard drive. I made a partition that was 10240MiB which should turn out to be 10GiB if my calculations are correct. GParted showed the partition as being 10GiB and all was well.

I then proceeded to reboot and put in my Windows XP CD so I could install Windows on the small 10GiB partition and then later dual-boot both Windows and Ubuntu. I noticed that on Windows the partition shows up as 9.99GB. Now, I know I am being picky, but this just didn't look right :D, so I put in the Ubuntu Live CD again and checked out what was going on with the partition. It turns out that GParted automatically checks the "Round to cylinders" feature and upon putting in 10240 as a value for your MiBs, it rounds it down to 10237MiB for my hard drive. I thought, "Oh! That's an easy fix, I'll just uncheck it." ... I was wrong. I get a recurring error if I uncheck the "Round to cylinders" option while putting in a value and then hitting the apply button. 

```

GParted 0.3.8

Libparted 1.8.9

Create Primary Partition #1 (ntfs, 10.00 GiB) on /dev/sda  00:00:00    ( ERROR )
     	
create empty partition  00:00:00    ( ERROR )
libparted messages    ( INFO )
     	
Unable to satisfy all constraints on the partition.

========================================

```
Currently there are no partitions on the hard drive, it's wiped clean. The only partition that I was trying to make / use was the 10GiB one. I am not sure what would be the cause of this error, because if I check the "Round to cylinders" option and put in 10240MiB it'll work and partition the drive, but then it will round it down to 10237MiB thus bringing me back to my plight :(.

Has anyone experienced this? Like I mentioned before, I know I am being rather picky, but I must say that this has got me quite intrigued (:

Thanks!

---

### Post by sendblink23 on 2009-01-12
Which way do you use Gparted?

through Commands or...  GUI ?

I've always used the GUI from the LiveCD, through in the TOP MENU, in Systems, inside Preferences or Administration, you shoudl read in one of them Gparted

And well that issue you are referring that has happened to you, I have never encountered anything like it.. actually Gparted for me has been perfect. And i have used it more than 8 times, I love to experiment with my hard Drive making random partitions, to install different OS's for testing.

By the way my current LiveCD is Ubuntu 8.10 also. 

> **Zacaretas said:**
> Hello!

I popped in my 8.10 Intrepid Ibex Live CD a few moments ago and started to use GParted 0.3.8 to partition my hard drive. I made a partition that was 10240MiB which should turn out to be 10GiB if my calculations are correct. GParted showed the partition as being 10GiB and all was well.

I then proceeded to reboot and put in my Windows XP CD so I could install Windows on the small 10GiB partition and then later dual-boot both Windows and Ubuntu. I noticed that on Windows the partition shows up as 9.99GB. Now, I know I am being picky, but this just didn't look right :D, so I put in the Ubuntu Live CD again and checked out what was going on with the partition. It turns out that GParted automatically checks the "Round to cylinders" feature and upon putting in 10240 as a value for your MiBs, it rounds it down to 10237MiB for my hard drive. I thought, "Oh! That's an easy fix, I'll just uncheck it." ... I was wrong. I get a recurring error if I uncheck the "Round to cylinders" option while putting in a value and then hitting the apply button. 

```

GParted 0.3.8

Libparted 1.8.9

Create Primary Partition #1 (ntfs, 10.00 GiB) on /dev/sda  00:00:00    ( ERROR )
     	
create empty partition  00:00:00    ( ERROR )
libparted messages    ( INFO )
     	
Unable to satisfy all constraints on the partition.

========================================

```
Currently there are no partitions on the hard drive, it's wiped clean. The only partition that I was trying to make / use was the 10GiB one. I am not sure what would be the cause of this error, because if I check the "Round to cylinders" option and put in 10240MiB it'll work and partition the drive, but then it will round it down to 10237MiB thus bringing me back to my plight :(.

Has anyone experienced this? Like I mentioned before, I know I am being rather picky, but I must say that this has got me quite intrigued (:

Thanks!

---

