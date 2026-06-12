---
title: "Dual-boot XP installation stupidity"
date: 2009-01-27
forum: General Help
---

### Post by sa3atsky on 2009-01-27
Hi, 2nd time I install Ubuntu and would like to Install it in a 50GB partition which already has Windows XP, therefore creating 10GB for Ubuntu and the remaining 40GB for Windows XP.
Should be easy right? All the guides say just choose "Guided - resize HD" and you can adjust the slider to suite your size.
if only it were that easy..
Ubuntu automatically selects another Partition, my 200GB Harddisk which has all my important backed up data and wants to partition it into 2 100gb slices.. I cant select the desired partition (50gb) I want in any way. When I chose manual it loads for 5mins and gives me this screen I have no idea what to chose, and no guide explains it claiming its for "intermediate to expert users"

Ubuntu really seems like fun, but these issues which could be easily fixed by putting a selector for the Partition you want in the Wizard would've made it a lot easier.

Anyway, hopefully someone has a solution to my problem, thanks.

---

### Post by sa3atsky on 2009-01-27
I booted into GParted and manually resized the partition to shrink Windows XP to 40GB and the 10GB left is unallocated space. 

Now how do I install Ubuntu in the 10gb partition to allow Dual-booting?

---

### Post by marcgh on 2009-01-27
Hi,
I had a sample problem on install and solved it with 'brute force' :

My machine has 3 HDD, and when I tried first time to install Ubuntu I was really confused (not finding my drive letters back).
I simply shut the machine down, disconnected all drives except the (C) drive where I wanted to install Ubuntu together with existing XP. I choosed guided and kept 40GB for XP and 80 GB for Ubuntu.
After install and restart, I plugged the other 2 HDD back in and all was working.
Maybee not the 'software' solution, but it worked for me and I was sure that nothinh could happen to my music & data on the other 2 HDD.

---

### Post by glennzo on 2009-01-27
> **sa3atsky said:**
> I booted into GParted and manually resized the partition to shrink Windows XP to 40GB and the 10GB left is unallocated space. 

Now how do I install Ubuntu in the 10gb partition to allow Dual-booting?

You need to choose that partition during the Ubuntu install. It will be obvious which partition it is because of it's smaller size. You also need to set that partition as / and have the installer / partitioner format it as EXT3. Once that's done the install will move forward.

---

### Post by sa3atsky on 2009-01-27
> **glennzo said:**
> You need to choose that partition during the Ubuntu install. It will be obvious which partition it is because of it's smaller size. You also need to set that partition as / and have the installer / partitioner format it as EXT3. Once that's done the install will move forward.

Did it exactly like that. Everything went fine and told me to reboot, when I did I was faced with the Windows Boot loader, which only had windows xP, and when I tried running it the PC suddenly restarted. Not only was Linux or grub not installed properly, but it actually ruined my Windows Installation as well. God I hope it didnt do anything else, for the love of God please fix your installation if you want people to experience a seamless transition to Linux, terrible installer + documentation

---

### Post by glennzo on 2009-01-27
> **sa3atsky said:**
> Did it exactly like that. Everything went fine and told me to reboot, when I did I was faced with the Windows Boot loader, which only had windows xP, and when I tried running it the PC suddenly restarted. Not only was Linux or grub not installed properly, but it actually ruined my Windows Installation as well. God I hope it didnt do anything else, for the love of God please fix your installation if you want people to experience a seamless transition to Linux, terrible installer + documentationQuite easily done by millions of Linux users. You now need to look into re-installing grub the Ubuntu way. Let's hope *you* didn't destroy your Windows installation.

---

