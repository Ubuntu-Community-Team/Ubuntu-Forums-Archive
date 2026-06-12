---
title: "inserting new hdd, need help"
date: 2006-09-23
forum: Desktop Environments
---

### Post by anatole on 2006-09-23
hi,
currently i have two hard disks, both ATA types, connecting on IDE. My partitions are:
hda: hda1 - windows xp, hda2 - ubuntu, hda3 - switch, hda4 - storage
hdb: hdb1 - storage.

i recently bought a sata type hard disk, and i tried it today - connected it to its own sata plug. i expected my comp trying to boot from it and awaited the error msg - yet i got grub, which surprised me a bit - even more when i found out that it cannot boot my ubuntu - i get the splash, and it hangs at "waiting for root filesystem" (after an unsuccessful "mounting root filesystem"). Windows XP boots well.
My guess was that the hard disks names have changed, so i tried manually editing grub (both the first line from "root hd0,1" to "root hd1,1" and the kernel line, from "root=/dev/hda2" to "root=/dev/hdb2", with no results. (when i changed the line "root hd0,1" to something else, i got the message that no such partition exists.)
What may be the problem, and how do i solve it? At first i'd like to use the sata disk as storage, maybe later i would like to make it primary and use it for my root partition, can i do that? i don't even have a basic understanding on what should be primary now (i can't see a way to manually set up an order between the disks) so any help would be appreciated, thanks :)

---

### Post by dexter on 2006-09-23
Your hard drive numbers will not change, the new sata disk will be recognised by Ubuntu and placed in /dev/sda. Your system is still at it's original place /dev/hda2, so you should not edit your grub file.

Actually, I am surprised that Ubuntu fails to boot after a simple procedure of adding a hard drive. Maybe it fails to mount the hard drive because 
- it has no sata drivers
- disk isn't formatted yet
- ...
However these are no reasons why your system doesn't boot. I'll be following this topic to see what the answer is...

---

### Post by orb9220 on 2006-09-23
adding a sata drive the bios sometimes changes the boot order of devices and makes the sata the first device. Check your bios.

---

### Post by dexter on 2006-09-23
> **orb9220 said:**
> adding a sata drive the bios sometimes changes the boot order of devices and makes the sata the first device. Check your bios.
True, but he sees the splashscreens and it hangs at mounting root filesystem, so he is booting his system.

---

### Post by orb9220 on 2006-09-23
Sorry about that must have let my cafeine level drop to low which effects my concious level.

---

### Post by gwk on 2006-10-03
I can't give you exact details on how to fix this, but I had the exact same problem when I added an SATA drive.  Whenever I add or take out a drive from my system, Ubuntu stops booting because of this error - very annoying.  And I get the same error as you mention - "waiting for root filesystem" or whatever, it was the second line to load in the GUI boot up screen.

You were on the right track with editing your bootloader settings.  What I did was load the Ubuntu Live CD again with all the normal drives connected and started an install so I could see which designations it gave each drive (sda1, sdb1, etc.).  Then I stopped the install, edited my grub settings replacing the sda with sdc or whatever it was I had to change.  Rebooted and Ubuntu loaded perfectly.

I think even having my iPod connected screws this up.  And when I updated the system to the Edgy (6.10) Beta it hosed the system again.  I dunno if this is a bug, or a known limitation.  If it's a bug, I'll submit it if someone lets me know where to do that.

Cheers,
Gregg

---

