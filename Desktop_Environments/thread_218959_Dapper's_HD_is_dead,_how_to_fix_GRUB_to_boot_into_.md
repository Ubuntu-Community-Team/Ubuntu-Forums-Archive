---
title: "Dapper's HD is dead, how to fix GRUB to boot into Win for now?"
date: 2006-07-19
forum: Desktop Environments
---

### Post by mjpatey on 2006-07-19
Sorry for the long subject line...

I have two hard drives in my system currently, the big one running Windows, and the smaller one running Dapper.

The Dapper one is set up as the Primary Slave, and is about to fail catastrophically (grinding noises, not being recognized by BIOS a good percentage of the time).

When the drive is wonky and doesn't get picked up by the BIOS, GRUB fails (since its setup refers to a currently non-existent drive, the dreaed "Error 21"), so I never have the option to boot into any OS.

The only way I've been able to get around this is by trying over and over, hoping the BIOS will eventually see the drive, and so far, it eventually does.

Until I have a replacement hard drive on which to reinstall Ubuntu [as soon as Seagate sends a replacement :-) ], is there some way for me to modify GRUB to ignore my Ubuntu install and just boot to Windows, so it doesn't hang when the secondary drive is dead?  As soon as possible, I have to remove the drive completely to send it back to be replaced, and I need some way to wipe out GRUB's knowledge of my Ubuntu installs on that drive so it won't hang every time I try to boot.  Or can I just uninstall GRUB somehow?

Thanks for any help you may have!

-Mark

---

### Post by mrbaz on 2006-07-19
Grub is going to be launching off of your ubuntu partition if I am not mistaken.

Pop in your windows CD and use the recovery console to fix your boot loader.  'fdisk /mbr' or something like that.

---

### Post by mjpatey on 2006-07-19
That's weird... if GRUB is located on the same drive as Ubuntu, then that means the drive is working enough to find GRUB, but then fails while GRUB is looking for OS installations.

Does that sound like I'm having some other problem besides a failing hard drive?

---

### Post by mjpatey on 2006-07-19
You know, I'm starting to think GRUB isn't located on the same partition as Ubuntu.  It doesn't make sense that it could be.

Since on my system, Ubuntu is on the "primary slave" drive, and my BIOS is set to boot from DVD first, then the "primary master", *then *the primary slave, wouldn't it stand to reason that GRUB (or whatever's causing GRUB to load) must be located on the primary master?  Otherwise, the system would just boot into Windows (the OS that booted by default on the primary master drive before GRUB was installed).

Please let me know if I'm wrong somewhere... I'm feeling my way around here!

In any case, is there any way to remove GRUB, or cause it to ignore the reference to my Ubuntu installation which is on a no-longer-working drive?  That way I can at least boot into Windows until my replacement drive arrives.

(I'm about to try mrbaz's recovery console idea shortly, if I can find my Win install disk.)

-Mark

---

### Post by Bagnaj97 on 2006-07-19
The way grub works is that the first part is loaded on the Master Boot Record of whichever is your master drive. This part then loads up another stage of grub from your linux drive/partition. If your disk with Ubuntu is dead the first part of grub should still load from the MBR. I think the only way to make the computer just boot into windows is to find a dos boot disk and type ```
fdisk /mbr
``` or if you have windows 2000 or XP boot the cd and enter the recovery console, then log in and use the fixmbr command

---

### Post by mjpatey on 2006-07-19
Thanks, all... I'll let you know how it went.  I'll be attempting this about 6 hours from now (when I have access to my XP install CD)!

-Mark

---

