---
title: "dell 530s with vista, crash after installing ubuntu 7.10 dual boot"
date: 2007-11-25
forum: Dell  Ubuntu Support
---

### Post by ness07cba on 2007-11-25
I failed to intall ubuntu 7.10 after partitioning the hd with the vista tool in my dell 530. I previously have been installed easyBCD as boot loader. I used alternated ubuntu cd to perform the installation. In the free partition I did two more partition: / and swap. After that, ubuntu send me an error about "unexpected" fat size of windows partition. Some blogs suggest that this error is expected in dell computer due to the fat16 partion of  dell utilities. The suggested action in those blogs is to ignore the warning and procede. As the last isntallation step, I indicated install grub NOT in the MBR, but in the / partition with flag B. When I reboot the system, an error messages appear in the screen, asking for a boot cd. It did not load neither vista or ubuntu. The solution (that is not a practical solution) was to reinstall vista and easyBCD.  After that, easyBCD had not problem to load the previously ubuntu installation (which was a proof that my action was right??). 

I need to repeat the dual boot installation in another 530 dell, but without such long way. Some suggestion???? :confused:

Thanks,

---

### Post by groovete on 2007-11-25
The easiest way I know is installing Ubuntu with the LiveCD (MS-OS has to be installed first) using the build in partitioning  tool. Finally you will have a dual boot with Grub as bootloader. No need using this MS stuff.

---

### Post by shashen on 2007-11-25
i did a duel boot install a couple of weeks ago without any problems after following the easy step by step guide on this site [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)     now i boot up vista maybe one a day for a couple of thigs to check out. Just a tip, if you ever run into trouble and have to install vista again open your pc and unplug your cables in front of the pc that goes to your memory cards and stuff otherwise you will have your primary HD as J drive wich will couse a couple of problems,,if you unplugg and install vista you will have your drive back to C. Good luck

---

