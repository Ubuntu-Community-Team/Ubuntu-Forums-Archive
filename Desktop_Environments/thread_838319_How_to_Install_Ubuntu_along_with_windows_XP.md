---
title: "How to Install Ubuntu along with windows XP?"
date: 2008-06-23
forum: Desktop Environments
---

### Post by mirchichamu on 2008-06-23
Hi! I am newbie here. I was Windows XP user. I want to install Ubuntu as well, along with windows XP ( Dual boot).I am in the process of downloading Ubuntu.It will finish in 3 hours time. What is the easiest way to do that?

My desktop is Pentium 4 3.00 GHZ. My hard disk is prepartitioned with 4 drives C,D,E and F. Total 80 GB's. Windows XP is installed on C drive.

I shall be thankful to you.

---

### Post by Dr. Octagon on 2008-06-23
You might check out this site, it has some pretty comprehensive info as well as screen shots of the various steps.  
[COLOR="Blue"]
**[How to dual boot XP and Ubuntu (XP installed first)]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm")**[/COLOR]

---

### Post by mirchichamu on 2008-06-23
> **Dr. Octagon said:**
> You might check out this site, it has some pretty comprehensive info as well as screen shots of the various steps.  
[COLOR="Blue"]
**[How to dual boot XP and Ubuntu (XP installed first)]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm")**[/COLOR]

Thanks a lot.
I have already gone through this site. They are telling how to make partition inside partition. My disk is already partitioned. How can I install in "suppose Partition D" of my hard disk.

---

### Post by Dr. Octagon on 2008-06-23
You might consider reconfiguring how your data is stored, i.e. minimize the partitions by combining the data from your other partitions into one (combine D, E, and F into one partition).  After doing this you will have a definitive location for installing ubuntu.

---

### Post by mirchichamu on 2008-06-23
Thanks Dr Octagon!
But I want to keep at least 3 partitions. Because I am having personal data on all.

---

### Post by Dr. Octagon on 2008-06-23
I did some looking around and found some other sites which you might check.

[B][http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html")

[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html]("http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html")[/B]

---

### Post by mirchichamu on 2008-06-23
Thanks once again. You have taken a lot of troubles to find solutions for my questions.
But unfortunately I couldnot find a solution. My question is straight forward. I am having 4 partitions already. I need not to partition again.
My question is can I install in my D drive without repartitoning my drive??

---

### Post by WeeWoh on 2008-06-23
You could do that yes (if I have read it right) Or you could install Ubuntu using WUBI. You just put the cd in while you are running windows then go "wubi.exe" on the disk. I have never used wubi so i cant tell you how to go from there.

---

### Post by Inferied on 2008-06-23
Use the "manual" option when partitioning, set the mount point of D as "/" and make a swap partition twice the size of your RAM, if it's not already there.

---

### Post by PeidGnourt on 2008-06-23
> **mirchichamu said:**
> Hi! I am newbie here. I was Windows XP user. I want to install Ubuntu as well, along with windows XP ( Dual boot).I am in the process of downloading Ubuntu.It will finish in 3 hours time. What is the easiest way to do that?

My desktop is Pentium 4 3.00 GHZ. My hard disk is prepartitioned with 4 drives C,D,E and F. Total 80 GB's. Windows XP is installed on C drive.

I shall be thankful to you.

---> Oh, my computer is same as yours. It's Pentium4 3Hz, 1GBRam, HD 80GB
If you want to install Ubuntu along with Windows XP, you just install it normal. It'll use a software called GRUB to manage your OS, so you can choose Windows XP or Ubuntu every time you start yours computer. Have fun!^^

---

### Post by PeidGnourt on 2008-06-23
> **Inferied said:**
> Use the "manual" option when partitioning, set the mount point of D as "/" and make a swap partition twice the size of your RAM, if it's not already there.

--> To my opinion, I think it doesn't necessary if you have about 512 MB Ram or up, my computer never use more than 450MB of Ram to run Ubuntu.

---

