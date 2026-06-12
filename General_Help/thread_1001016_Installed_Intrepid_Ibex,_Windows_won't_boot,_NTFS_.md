---
title: "Installed Intrepid Ibex, Windows won't boot, NTFS partition not readable,"
date: 2008-12-03
forum: General Help
---

### Post by liquidcola on 2008-12-03
I just installed Intrepid Ibex on my acer aspire one laptop. Everything went smoothly, ubuntu boots fine, all is good. BUT! When I choose Windows XP from my grub menu, it says something to the effect of "loading" for about 1 second, and then spits me back to the grub menu. There is another option for windows which is an OEM recovery mode on a separate partition that boots up fine. When I go into gparted, my main NTFS partition shows up, but has a yellow triangle with a "!" inside it next to it, and says the partition is unreadable. Did the installation somehow kill my NTFS partition? 

fdisk -l gives me this:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         637     5116671   12  Compaq diagnostics
/dev/sda2   *         638       10246    77184292+   7  HPFS/NTFS
/dev/sda3           10247       14593    34917277+   5  Extended
/dev/sda5           10247       14409    33439266   83  Linux
/dev/sda6           14410       14593     1477948+  82  Linux swap / Solaris


sda2 would be my windows partition, but what's with the HPFS? I think I told grub to put it's files on that partition during the install, did it write to an NTFS partition using HPFS somehow? 


Any help would be GREATLY appreciated, all my data is in that partition and because my ubuntu installs have always gone super smooth, I didn't back anything up this time. #-o

---

### Post by Titan8990 on 2008-12-03
You should have wrote grub to the MBR (like it suggests).


Download supergrubdisk and attempt to install grub to the MBR from there.

---

### Post by caljohnsmith on 2008-12-03
If booting Windows causes you to get thrown back to the Grub menu, that is usually a classic symptom of having accidentally installed Grub to the boot sector of your Windows partition. Do you have a Windows XP Install CD? If so, boot that, go to the "recovery console" and run:
```
fixboot
```
And that will fix the problem if Grub was accidentally installed to the XP partition boot sector. If you don't have a Windows Install CD, you can instead download a Windows Repair CD from [here]("http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip"). How about trying the above command and let me know if that does the trick. :)

---

