---
title: "Jaunty install created a messed up grub install."
date: 2009-05-03
forum: General Help
---

### Post by jwbrase on 2009-05-03
About a week ago I upgraded from Intrepid to Jaunty. Jaunty failed pretty soon, but not immediately, after that, so I decided to do a fresh install of Jaunty from a live CD, and if that didn't solve the problem, to go back to Intrepid. Unfortunately, when I installed Jaunty from the live CD it didn't install grub properly, and now my system is a total mess.

I installed Jaunty to the external hard drive I'd had Intrepid on (I migrated Intrepid from a Wubi install), and Grub seems to have been installed to that drive by the Jaunty installer, but it fails at stage 1.5 with error 15 if I boot from that drive.

I eventually gave up on trying to boot Ubuntu tonight and decided to leave it for the morning. That's when the real shock hit. With Intrepid, I'd had it set up so that the BIOS would check the USB ports before the internal drive, and then Grub would load off of the external drive and boot whichever OS I selected from the menu. If I selected XP, it would hand off to the internal drive. That way if I disconnected the external drive, the machine would behave as a single boot machine and load straight into XP, and if I had any boot-related problems with Ubuntu, they'd be isolated from the XP side of the machine. 

Well, once I gave up on getting Ubuntu running tonight, I decided to boot into XP and do a few things there. So I switched the BIOS to boot from the internal drive, intending to leave it there until I got Jaunty working. Much to my surprise, I got a working Grub menu. I was not impressed. Yes, I wanted to get Grub working and get into Jaunty, but, no I did *not* want the installer to even *touch* the internal drive, let alone install Grub to it. Oh well, it was annoying, but as long as everything works, I can reconfigure things later, right? Well, I selected WinXP from the menu and hit enter. And Grub returned error 11. So I rebooted and selected Jaunty from the menu. At least that worked. And at least when I mounted and browsed the drive in Jaunty all the data on it seemed to be intact. 

But I don't really know how to go about removing Grub from the MBR of the internal drive, where it seems to have been installed, and restoring the XP bootloader. So any help along those lines would be great. Also, if there's any install options I missed that could have given me more control over where grub went, I'd be glad to know.


[rant]
I can handle it if I need to mess around with Grub a bit to get things working, that comes with the territory of being a newbish Linux nerd, although it's annoying that Jaunty can't install its own bootloader properly. What really irks me though, is that after hearing people smirk about how Windows overwrites the MBR of the drive it's installed on if it finds a non-Microsoft bootloader, *and after having smirked at that myself*, I find that Jaunty has done the exact same thing to my computer, on a drive it wasn't even told to *touch*. (I made quite sure that I was installing Jaunty to the external drive and wasn't making any changes to the internal one). My Dad bought this machine to use as our new primary home machine, but is wary about trusting a dual boot machine with our data. I thought I had resolved that by isolating Grub and Ubuntu from XP by placing them on the external drive, which could be unplugged at any time, but if I can't trust the installer not to write to drives it's not told to write to, I'm not sure he can trust a dual boot machine with our data. And if that's the case, I'll either have to take our older machine and install Xubuntu to that, which I'm not sure I want to do, or else wait until I can get myself a System76 Laptop. (Which I could theoretically afford, but it would be a real wallop to my bank account). Which means I may have to give up Ubuntu for a while, or use it on a really old and slow machine, and that makes me mad...[/rant]

---

### Post by delcypher on 2009-05-03
You have two options.

1. Use the windows XP setup CD and go into the recovery console and run```
fixboot
fixmbr
```. In that order, then reboot and now your system when booting from your hard drive will boot from windows. [Click here for a guide on this]("http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/")

2. Modify GRUB's menu.lst (/boot/grub/menu.lust) and add a chainloader entry at the end of the file.

```
title           Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

the (hd0,0) part is important and is unique to your machine. It is the location of windows XP on your hard disc(s). It is in the following format (hd[HARD_DRIVE_NO],[PARTION_NO]) where [HARD_DRIVE_NO] and [PARTION_NO] start from 0. So for example my 1st hard disc second partion would be (hd0,1).

For more information on this look at [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5") 
and 
[http://www.gnu.org/software/grub/manual/grub.html#Naming-convention]("http://www.gnu.org/software/grub/manual/grub.html#Naming-convention")

Oh in response to your rant yes okay so the UBUNTU graphical install wrote on your boot partition, you can tell it not to, you just need to know where the option is. If you look [here]("https://help.ubuntu.com/community/GraphicalInstall") (step 14.) there is a button labeled advanced. If you click it you get (see attachment)

---

### Post by jwbrase on 2009-05-03
OK, good to know that that option is there under "advanced." I do wish that it were on the main screen there though.

---

### Post by jwbrase on 2009-05-03
The other question, of course, is how I would go about getting Grub to load properly on the Ubuntu drive. It throws error 15 when I try booting from that drive.

---

