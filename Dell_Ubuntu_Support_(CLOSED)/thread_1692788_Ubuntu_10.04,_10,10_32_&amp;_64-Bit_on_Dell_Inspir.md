---
title: "Ubuntu 10.04, 10,10 32 &amp; 64-Bit on Dell Inspiron M5010"
date: 2011-02-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Captainnow on 2011-02-21
I'm trying to run ubuntu on a dell inspiron 5010. 

AMD Triple core 2.3 
6 GB Ram
640 GB Hard drive (40 GB for Ubuntu 3GB Swap)
Intergrated ATI Mobility Radeon
Broadcom wireless card

My issue is this. I can only get 10.04 64-Bit to install.
When it is installed it loads EXTREMELY slow. 
It takes 1 minute 30 seconds for the log on screen to load from the OS selection screen.
After logging in it takes another 3+ minutes for the menu bars to load so I'm finally able to do something.

This seems like a very long time. When I can get Windows 7 to load in 1 minute 41 seconds. That is from the OS selection screen to a fully loaded desktop and all startup applications loaded. That is even time with me typing in my password. I paused the time to type in password in the above times for Ubuntu.
Also the Ubuntu install is just the OS. I have no extra apps installed beyond what Ubuntu installs itself.

When I try to install 10.04 32-bit or any version of 10.10 the installer doesn't even load. It shows the splash screen and then freezes and goes no further. I have used burned CDs and have also used bootable flash drives. None will even load to try other versions of the OS to see if they boot up faster.

I would certainly like some tips to get ubuntu running better.

---

### Post by frankduffey on 2011-02-22
> **Captainnow said:**
> I'm trying to run ubuntu on a dell inspiron 5010. 

AMD Triple core 2.3 
6 GB Ram
640 GB Hard drive (40 GB for Ubuntu 3GB Swap)
Intergrated ATI Mobility Radeon
Broadcom wireless card

My issue is this. I can only get 10.04 64-Bit to install.
When it is installed it loads EXTREMELY slow. 
It takes 1 minute 30 seconds for the log on screen to load from the OS selection screen.
After logging in it takes another 3+ minutes for the menu bars to load so I'm finally able to do something.

This seems like a very long time. When I can get Windows 7 to load in 1 minute 41 seconds. That is from the OS selection screen to a fully loaded desktop and all startup applications loaded. That is even time with me typing in my password. I paused the time to type in password in the above times for Ubuntu.
Also the Ubuntu install is just the OS. I have no extra apps installed beyond what Ubuntu installs itself.

When I try to install 10.04 32-bit or any version of 10.10 the installer doesn't even load. It shows the splash screen and then freezes and goes no further. I have used burned CDs and have also used bootable flash drives. None will even load to try other versions of the OS to see if they boot up faster.

I would certainly like some tips to get ubuntu running better.
reinstall 10.10 try using WUBI to install from the CD go to WUBI and run the install be sure to remove the current version and then try and see if you have the same problem I am still learning Ubiuntu however I am A+ Certified Technician COMP TIA and Also Norvell Network Certified. I had my own Computer Business with a partner in St peters-burg fL FOR OVER 10 years. I hope this helps. I did not like the VM ware installers for windows baiscly they suck. WUBI is much more effective for a dual boot install. You can update your Install from update under the administration .
         I am still learning Linux but so far I have found that I like the command line in terminal remind me of the old MS dos you had to load 13 disk for windows 3.1 I also worked for the City of Pineless Park as a MIS Technician I ran the AS/400 IBM Main Server and the Police Department Server Backups and configurations for citywide systems They did go to a no Computer type network with the NT server running off NT Server Card on the AS/400 If you have any other problems send me a message on here. I do have a question I did a reinstall of Ubuntu and when I boot of the Boot Manager shows 2 Ubuntu Selections So how do I remove this from a  command line?

---

### Post by Captainnow on 2011-02-23
I would prefer to run Ubuntu outside of windows on it's own partition since that is how I have my computer set for. 

I already have 10.10 64 Bit running in a virtual machine using VMware.

Ubuntu I would think should work just find on a duel boot machine without taking 3 to 5 mins to load before I can use it.

Anyone have more information for me please? I have tried adding a pci=noacpi to grub at boot. That didn't affect the speed of loading Ubuntu at all.

---

