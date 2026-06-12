---
title: "Dell XPS 410n partition help"
date: 2007-10-11
forum: Dell  Ubuntu Support
---

### Post by Louis Cypher on 2007-10-11
I was just wondering about making a /home partition.  I have a Dell preloaded with Feisty.  There is a feisty image on one of the partitions to reinstall.  Does anyone know if using that image wipes all partitions and does the Dell default or no.  I just don't want to go thru the trouble of moving my /home directory to it's own partition and have it wiped out by the Dell image.  I know I can use a separate install disk so that is an option.  I'll have to look for some instructions on making a /home partition now :)  Thx for any help

---

### Post by dondad on 2007-10-13
> **Louis Cypher said:**
> I was just wondering about making a /home partition.  I have a Dell preloaded with Feisty.  There is a feisty image on one of the partitions to reinstall.  Does anyone know if using that image wipes all partitions and does the Dell default or no.  I just don't want to go thru the trouble of moving my /home directory to it's own partition and have it wiped out by the Dell image.  I know I can use a separate install disk so that is an option.  I'll have to look for some instructions on making a /home partition now :)  Thx for any help

I did exactly that. I repartitioned to get a separate /home. I didn't want to take the chance on their partition, so I reinstalled from the ubuntu iso. The only issue I had was that it would hang on the splash screen on a restart (shutdown was ok). I added "reboot=b" to the grub kernel options and that fixed it. I made the change permanent through kernel upgrades by adding the parameter to the default kernel options in the grub menu.lst file.

I am now running the Gutsy beta with updates and it is running great.

---

