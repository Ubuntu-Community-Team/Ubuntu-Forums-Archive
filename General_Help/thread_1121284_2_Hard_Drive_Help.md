---
title: "2 Hard Drive Help"
date: 2009-04-09
forum: General Help
---

### Post by risknothin on 2009-04-09
here is how my system is setup: 1st hard drive 3 partitions
 1. windows partition - dont want to use w/ ubuntu
 2. ext3 partion - free space
 3. swap
 
2nd hard drive is 1 partition - where linux is installed and all my files are held

- it seems for some reason that i am unable to use the 2nd partion on the first hard drive - everything saves to the 2nd hard drive which is now full and i need to use the other linux partition

- how do i go about mounting it or at least having a folder on my desktop to the drive?

Thanks for your help

---

### Post by FrankT-Qc on 2009-04-09
From the panel, go to Places->Computer. Your partition should be there.

If not, you could install gparted and check what's going on there... Be careful though, if you're not careful with that, you could break your windows

---

### Post by risknothin on 2009-04-09
i can see both hard drives in gparted - i tried to make sure it was formated in ext3 which it is. but for some reason its still no available

---

### Post by dcstar on 2009-04-09
> **risknothin said:**
> 
......
- **how do i go about mounting it** or at least having a folder on my desktop to the drive?

Thanks for your help

Install the **pysdm **package.

---

