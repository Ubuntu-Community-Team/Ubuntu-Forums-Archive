---
title: "Installed Ubuntu, ran GParted now space used is changed?"
date: 2009-06-02
forum: General Help
---

### Post by fuzzylogic25 on 2009-06-02
Hi, 

I just installed Ubuntu, and I already had windows XP in a separate partition. This is my first time installing Linux.

I have a 500GB drive, 20GB is a primary NTFS partition for win xp. I set linux to use the remaining space at installation time. Once installed, I checked the properties of the parition linux is using which is called "Filesystem" through File -> Properties and it said the following:

Ubuntu filesystem properties
---------------------------------------------------------------
Hard disk space used: totalling 3.2GB (some files unreadable)
Freespace: 409.5GB
---------------------------------------------------------------

Then i ran Gparted, because I actually only wanted 30GB for the parition, and remaining space to be used as data partition which will be NTFS. Gparted stated following information when i ran it:

What GParted saw before making any changes
---------------------------------------------------------------
/dev/sda1   : ntfs         Size:19.53G; Used: 11.11G; Unused: 8.42G; boot flag
/dev/sda2   : extended  Size: 446.23GB
         /dev/sda5   ext3 Size: 440.47gb; Used: 8.97; Unused: 431.51
         /dev/sda6   linux-swap Size: 5.75gb
---------------------------------------------------------------

Then what I wanted to do was set /dev/sda5 down to 30GB, and move the /dev/sda6 (linux-swap) to just after the /dev/sda5. That way, the remaining space which is going to be data partition in NTFS can be put at the end of disk.

So this is what I set the conditions to be:

Changes I wanted to make: (resize ext3 partition down and move linux-swap from end of disk to just after ext3 partition)
---------------------------------------------------------------
/dev/sda1   : ntfs         Size:19.53G; Used: 11.11G; Unused: 8.42G; boot flag
 /dev/sda2   : extended  Size: 446.23GB
          /dev/sda5   ext3 Size: 29.29GB; Used: 8.97GB; Unused: 20.33GB
         /dev/sda6   linux-swap Size: 5.75gb
         new partition #1 411.18
---------------------------------------------------------------

After I ran this process, i got the following information form GParted:

GParted view on disk partitions after I made changes
---------------------------------------------------------------
/dev/sda1   : ntfs         Size:19.53G; Used: 11.11G; Unused: 8.42G; boot flag
  /dev/sda2   : extended  Size: 446.23GB
           /dev/sda5   ext3 Size: 29.29GB; Used: 2.49GB; Unused: 26.8GB
          /dev/sda6   linux-swap Size: 5.75gb
          new partition #1 411.18
---------------------------------------------------------------

And when I when I booted up Ubuntu to check the properties of the FILESYSTEM disk like it did initially I got:

---------------------------------------------------------------
Hard disk space used: totalling 2.6GB (some files unreadable)
 Freespace: 25.3GB
---------------------------------------------------------------

My question is, after I did a resize, why has the space used according to Ubuntu changed from 3.2GB down to 2.6GB? Have I lost some data that was there from the installation process?

And according to GParted, why does it say the used space was 8.97GB for that drive but now saying 2.48GB? Have I lost that much data?

---

### Post by MichaelSammels on 2009-06-02
Open Disk Usage Analyser, click Edit and Preferences and set it to scan only /dev/sda5, which will provide a more accurate output of Disk Usage information. Post results here, in a codebox if possible.

---

### Post by fuzzylogic25 on 2009-06-02
disk usage analyser says it is 2.1GB when just installed and after i run GParted, it said 2.0GB used. When i tried to set the preferences to just the sda5 drive it was already set. Actualy, that was the only one that could be seen (/dev/sda5/). the others wont listed. is that a problem?

So what do you think is wrong with all these different disk usage statistics. I thought a fresh install of ubuntu was suppose to be 8GB? I was never connected to the net while i installed, and still havnt. is that a priblem? coz some common apps like vim, emacs appear to be missing.

---

