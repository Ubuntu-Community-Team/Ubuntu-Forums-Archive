---
title: "From dual boot to &quot;dual computers&quot;"
date: 2005-11-01
forum: Desktop Environments
---

### Post by Snewton on 2005-11-01
Hi!

I'm currently running dual boot with xphome and breezy. They are innstalled on two different drives. I want to move one of the drives to another computer, having one breezy and one xp-machine.

First I think I'll remove the breezy disk. Then:
> restore the windows xp boot loader by booting from the windows xp cd when it boot's up choose recovery console, and when you get to the command prompt type fixmbr this will remove grub and replace it with the default windows bootloader

Then the xp-drive should be ok (or?)

Then I hope the breezy boots as normal, but without GRUB (or?)

The breezy disk will be on the same motherboard, but with different cpu and graphics card. The disk will be master, not slave. The xp-disk will be at a new motherboard, but with same cpu and master as before. 

Can anyone confirm that this is the right procedure, or correct any misunderstandings? And if there are any other issues a newbie could expect, please tell me (problems with changing slave/master f.ex.)....

I also wonder how to get a "fresh" breezy install, is it just to use a installation-cd, as in windows?

---

### Post by Kyral on 2005-11-01
Where was GRUB installed before (Which disk is the master right now basically)

---

### Post by Snewton on 2005-11-01
The xp-disk is master, and I guess the GRUB is in MBR, which means it is on the same drive as xp (or?)....

---

### Post by NewWithoutClue on 2005-11-01
Maybe i'm wrong but..i think you still need a bootloader to boot linux.
the installation disk will help you with that; take a look at the menu.

Regards,
Paul.

---

### Post by Kyral on 2005-11-01
Yah means GRUB is on XP's MBR. I think you can do it, but you are going to have to use a LiveCD to recover GRUB on the Breezy disk before you boot it. It *looks* right, but you never know

---

### Post by Snewton on 2005-11-01
Ok, I'll give it a try tomorrow (it's late night in Norway now). But do I have to use a live-cd? Does'nt an install-cd do the job?

---

### Post by NewWithoutClue on 2005-11-01
it should, just go to the menu ( hit esc when it's done loading ( at the partiton part ) ) then there should be a selection labled something related to your query.

you might need to give it some information, but i'm not sure.


w00t,
Paul.

---

### Post by SilentCacophony on 2005-11-01
You may do rescue operations if you type in 'rescue' when first prompted by the install cd. You may want to look for the *HOWTO: Restore grub...* here in the customization forum.

I'd say you'd have to restore the MBR on the XP drive for sure, since the menu.lst is probably on the other drive, which won't be there anymore.\

You'd probably have to restore grub to the ubuntu drive's MBR, unles you'd done it previously. I do believe that you can do that before the move as well...

You'll likely have to reconfigure xorg on first boot for ubuntu, as well. I simply don't know how a different cpu would affect things, though. Hopefully it'd be fine.

---

### Post by wammy on 2005-11-01
getting ubuntu to boot you might do the following:
before you switch harddrives boot into ubuntu.
-burn a boot cd (boot floppy's dont work with 2.6 kernels (too big for floppy))
you can make one witk mkboot and specify to write to iso format and burn that or maybe you can use mkrescue --iso (dont remeber exactly... long time ago)
- take xp hdd out.
- connect ubuntu disk to ide1
- boot from cd
- run grub-install /dev/hda (not exactly sure about exact options)

voila

next step, xp hdd:
- get/make a bootable dos floppy.
- boot from floppy
- then do:
fdisk /mbr
- reboot

and all should be well...

try at own risk ;)

---

