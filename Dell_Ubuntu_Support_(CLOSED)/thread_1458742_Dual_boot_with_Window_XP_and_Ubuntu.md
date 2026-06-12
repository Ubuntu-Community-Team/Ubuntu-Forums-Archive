---
title: "Dual boot with Window XP and Ubuntu"
date: 2010-04-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by milkyway538 on 2010-04-20
I am a beginner with Ubuntu and I have a problem with dual boot XP & Ubuntu.
My system: Dell portable Inspirons (1.6GHz, 1G RAM, 60GB HD) with Window XP and an external HD 500GB
I have recently installed Ubuntu v9.10 from live CD on the external drive (USB connected to PC). I use the menu driven installation (WUBI method, provided by the live CD) and I selected the external drive as the place for Ubuntu. I did not do any partitioning on this external drive before hand.
 
After installation, when power up the system (reboot) I see the option Ubuntu after the XP (as expected !), but after selecting Ubuntu, the system does not start up Ubuntu but it goes to grub> command screen.
 
Then by chance I have found out that if I type the command:
grub> reboot (hd0,2) then the system reboots and choosing Ubuntu option again will properly boot my PC into Ubuntu enviroment  ... i.e. I can see different kernel versions (generic mode, recovery mode etc...) and then Ubuntu runs correctly :-)
 
Now my question is: 
1) how can I get rid of the intermmediate process of typing the command 'reboot (hd0,2)' when I expect the system should boot correctly from the first try ?
someone tells me the problem may lie with USB detection when first power up ??
 
2) After I experiment with changing the grub> command to 'reboot (hd1,1)' when I encounter the first boot issue (mentioned above) in order to see understand the issue.
 
However after rebooting with this command, the first Kernel option on the list (version .20 (generic) does not work anymore (error message of synchronisation to hard disk ??!!)
 
So I go back to reboot with command 'reboot (hd0,2)' and then choose the older kernel version (.14 generic)) and Ubunti works again.
 
So how can I correct the first Kernel version ?
 
Thanks before hand for help

---

