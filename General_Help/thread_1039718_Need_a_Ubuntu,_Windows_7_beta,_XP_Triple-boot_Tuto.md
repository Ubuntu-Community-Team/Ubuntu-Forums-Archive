---
title: "Need a Ubuntu, Windows 7 beta, XP Triple-boot Tutorial"
date: 2009-01-14
forum: General Help
---

### Post by Wangsta on 2009-01-14
So I'm needing to make a triple-boot with Windows 7 beta, Ubuntu, and XP.
I've found a lot of Ubuntu/Vista/XP tutorials and even some Vista/7 Beta/Ubuntu tutorials, but I can't find any for 7 Beta/XP/Ubuntu!

Does anyone have a link to one such tutorial?
Or perhaps can explain step-by-step themselves?

---

### Post by Zevik on 2009-01-30
I recently did the same to see what the W7 hype was all about, although I ended up removing Windows 7 after a few days cuz I needed the HDD space. I'm pretty sure here is what I did. If you need an additional resource, you can use the [apcmag.com dual-boot guides]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm") and adjust accordingly.

Download and burn GParted Live (just do a google search) to a CD and boot your computer. Use GParted to create a new partition (at least 10-15 GB) for W7. Make sure it is associated with the XP partition so that the W7 boot loader will recognize XP. When you boot W7, it will give you the option to boot XP as the "Earlier Version of Windows."

Then, you either need to adjust the W7 boot loader with EasyBCD (instructions can be found on the apcmag guides) or, preferably, reinstall the GRUB Boot loader by doing the following:

Insert the Ubuntu Live CD (or flash disk or whatever) and select "Try without changes to computer." Once it loads up, open a terminal and type "sudo grub"

Then enter the following commands in order.

- root (hd0,0)
- setup (hd0)
- quit
- exit 

Reboot, and it will go directly back to Ubuntu. Now you'll need to edit GRUB to get the Windows partitions. You have two options - enter BOTH Windows partitions into GRUB, or just enter W7, and use the W7 bootloader to then select XP. To edit  grub, key into the terminal "sudo gedit /boot/grub/menu.lst" (or replace gedit with whatever program you prefer) and make sure that the option "hiddenmenu" has a '#' in front of it to make it visible. Then go to the very bottom where all the Ubuntu kernels are listed and add the following (NOTE: The location (hdX,X) may be different for your install):

title Windows XP
root (hd0,1)
makeactive
chainloader +1 

title Windows 7
root (hd0,2)
makeactive
chainloader +1 


That's pretty much what I did. Like I said, the apcmag guides were really helpful for me, I hope this post is what you were looking for. (If it is I may just add this as a guide on my blog...)

---

### Post by benner on 2009-09-24
Are they on different physical drives?  If so, then I think you can do the following:
-install xp (if that isn't what you are already running...)
-disconnect the xp drive and install 7
-reconnect the xp drive  
-run your ubuntu live CD and run the installer.  it should find the other 2 OS's and set up grub for you

I think as long as XP and 7 are on different physical drives then you can do it this way.  You can install Ubuntu to either of the drives and it will take care of the repartitioning when it installs.  You will see when you get to that step in the installation, it will show you the partitions and ask you what you want to do.  You can click and resize etc...  And if you get nervous at that point in the process, you haven't yet made any changes to your hard disks, so you can just cancel the install.

---

### Post by gravh on 2009-10-03
i had a problem but maybe this not a problem
i have instaled win XP then Ubuntu 9.4 then last Win 7
but in grub i dont have Win 7 boot choice for understand i draw my grub like this i hope you can get it

-Ubuntu lalal
-Ubuntu lalal safe
-Memtest
-Another OS
-XP
  *boot for XP
  *boot for 7

can you solve this problem

---

### Post by eshwar_andhavarapu on 2009-11-08
Hi just a quick suggestion. I believe if you install in the following order you won't have any problems and any tinkering to do with GRUB. The menu.lst option might work for Grub 1 but I am not sure it does for GRUB 2 which installs as standard with Ubuntu 9.10 for new installs. So anyway install.

1. Windows XP,
2. Windows 7/Vista
3. Ubuntu (or maybe other linux distros)

In this order the logic is that Windows XP will install first without any issues. Then when Windows 7/Vista installs it modifies the bootloader (boot.ini or something else) so that both of them show up. Finally, when ubuntu installs, it should pick up the presence of the other two and prepare GRUB accordingly. When that's done, you got nothing to do. I believe this way, GRUB links to the windows bootloader and that gives you the option to choose between the two windows versions.

---

### Post by eshwar_andhavarapu on 2009-11-08
Also, if you got windows 7 with xp mode (i think ultimate or professional) you might wanna skip installing windows xp altogether. Well it works for program compatibility purposes.

---

### Post by Z2. on 2009-11-19
> **eshwar_andhavarapu said:**
> Hi just a quick suggestion. I believe if you install in the following order you won't have any problems and any tinkering to do with GRUB. The menu.lst option might work for Grub 1 but I am not sure it does for GRUB 2 which installs as standard with Ubuntu 9.10 for new installs.

Grub 2 is waaaay different to Grub, you will need to read the tutorial on Grub2 before you try fiddling with it! I am no expert but I think Grub 2 does not wotk on booting more than one Win O/S, so you can set it up to boot to your Vista/Win7 boot loader, and boot WinXP from there, any WinXP boot issues you will have to resolve from the Win7 boot loader.

I wouldn't mind getting the triple boot sorted as I need both Win O/Ses but want to keep Ubuntu too, at the moment I boot to Grub 2 which defaults to Vista boot which lets me boot XP :(

---

### Post by holiday on 2009-11-19
VirtualBox might be good enough. Not sure what you need. I run two versions of Windows, Solaris, and four flavors of Linux in VirtualBox.

Running resource-hungry apps - like 3-d games - is frustrating, but for most other work the performance is as I expect from a native OS.

---

### Post by navin102 on 2009-12-28
--------------------

---

