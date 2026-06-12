---
title: "Running ubuntu on system with two hard drives"
date: 2020-04-21
forum: Desktop Environments
---

### Post by steve.clay on 2020-04-21
Hi, 

Thanks to both of the people that answered the question below. However, I am worried that OldFred said "Issues are common across many Dell models.". Oh dear. Is there a better choice of supplier / manufacturer? Perhaps I need to ask a new question for this? I have an old Acer machine that already has problems, buying a new one from someone else is meant to result in a system that works!

Original question:
I am thinking of buying a Dell  Inspriron 3471. It has a 25gB SSD to boot from and a separate 1TB SATA hard drive. I was thinking of putting all the software on the SSD disk and my data on the other drive. However, I have never used Ubuntu on a machine with two separate drives: will this be tricky to do?

Will I have to manually mount the second drive each time i start the machine and unmount, and perhaps stop the disk, again all manually each time? I don't want to buy hardware that will be difficult to use and especially if I could damage the disks or the data on them by getting the use of them wrong. Any thoughts or knowledge on this?

I have tagged this with 'drive and partition choices' because my default thinking is that I will have one partition on each disk but again, there might be better options?

---

### Post by CatKiller on 2020-04-21
> **steve.clay said:**
> It has a 25gB SSD to boot from and a separate 1TB SATA hard drive. I was thinking of putting all the software on the SSD disk and my data on the other drive. However, I have never used Ubuntu on a machine with two separate drives: will this be tricky to do?

Not in the least. Personal settings and data are stored in the user's home directory. Having /home as a separate partition is a pretty standard configuration. There are instructions and descriptions all over. Basically, during the installation pick "Something Else" and say that you want your SSD mounted at / and your HDD mounted at /home and the installer will take care of the rest. It's also pretty straightforward to do it post-install, too - just put the files in the right place and edit one config file.

---

### Post by oldfred on 2020-04-21
+1 on Catkiller's suggestion.

I normally create 25 to 30GB  for / (root). And my new (for about a month) install of 20.04 is using 8.3GB. It has had large updates every day as in process of being released in just a couple of days. But I also run a script to both update & houseclean so it has not grown much. I have not installed all the software I install, but have just about everything I use on a daily basis.

My older 16.04 & 18.04 installs were about 12GB with a lot of software installed after two years.

I do keep /home inside /, but move all data into data partitions. 

Issues are common across many Dell models.
Dell typically needs UEFI update, if SSD also SSD firmware update.
It needs UEFI setting for drives changed to AHCI, not Intel RST nor RAID. But if dual booting with Windows you must first install AHCI drivers into Windows or it will not boot.
Often better to have UEFI Secure boot off. And UEFI fast boot off, as that assumes no system changes & you are changing system.
Older Dell seemed to need legacy on, but still select UEFI to boot (without secure boot). Newer systems need legacy off to boot in UEFI mode.
And in Windows you need Windows fast start up off as that sets hibernation flag and then Linux NTFS driver cannot see the NTFS partitions. Note that Windows updates may turn fast start up back on.

Dell  Inspiron 3670 UEFI update & AHCI worked
[https://ubuntuforums.org/showthread.php?t=2412152](https://ubuntuforums.org/showthread.php?t=2412152)
Dell Inspiron 3567 Review i3 7100u (Works well)
[https://ubuntuforums.org/showthread.php?t=2364642](https://ubuntuforums.org/showthread.php?t=2364642)
Dell Precision 3520 Turn off RAID & change to AHCI
[https://askubuntu.com/questions/1096492/installing-ubuntu-18-04-alongside-windows10-the-ssd-is-not-recognized](https://askubuntu.com/questions/1096492/installing-ubuntu-18-04-alongside-windows10-the-ssd-is-not-recognized)

---

### Post by steve.clay on 2020-04-22
OldFred, thank you so much for your detailed reply. It terrifies me! However, I have just seen your answer to my question specifically about updating UEFI so I realise that I just need to understand heaps more about the terminology and the possible ways of doing what is needed if I buy the Dell and need to update UEFI.  I will read the links your included and meanwhile mark this question as solved. Thank you. (Maybe I will start a new thread on which hardware is best for Ubuntu!)

---

### Post by oldfred on 2020-04-22
I have seen many systems with UEFI since 2012. And Dell seems to be one of the better ones.
But the issues it has just require certain settings up front.
Other vendors like HP or Sony make it very difficult to dual boot, but if willing to live with some minor issues they also work.

I would only consider laptop that is on  the fwupdate list.
But most motherboards just work, even though most also say they do not support Linux. I prefer desktops unless you really have to have portability and for that occasion use, I use phone or my wife's ipad. But I am now retired, so not having to take work home.

---

