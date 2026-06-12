---
title: "BIOS lost on netbook"
date: 2009-03-11
forum: General Help
---

### Post by danbuter on 2009-03-11
I was trying to install Zenwalk from a flash drive onto my HP Mini, and it didn't work (due to not finding a CD drive). And it managed to delete my BIOS. Is there a way I can install this from a flash drive, or am I going to have to buy an external DVD player?

---

### Post by madverb on 2009-03-11
That doesn't really make much sense. Can you explain exactly what happened?

---

### Post by danbuter on 2009-03-11
I was in the installer, and it could not find a cd drive, so it wouldn't let me finish installing. I had already formatted the drive. Then the installer crashed or something, so I had to Ctl-Alt-Delete to shutdown my computer. When I rebooted, it gives me the choice to F10 to change boot order, but then goes to a black screen saying there is no OS.

---

### Post by MysticGold04 on 2009-03-11
> **danbuter said:**
> I was in the installer, and it could not find a cd drive, so it wouldn't let me finish installing. I had already formatted the drive. Then the installer crashed or something, so I had to Ctl-Alt-Delete to shutdown my computer. When I rebooted, it gives me the choice to F10 to change boot order, but then goes to a black screen saying there is no OS.

It didn't delete your Bios, but it sounds like it did wipe out your partition tables/OS.  You might be able to boot off of a Ubuntu memory stick to check on your partitions.  Do you have another machine to create a bootable stick on?

---

### Post by madverb on 2009-03-11
BIOS should be fine. Sounds like something has gone wrong with Grub. You can install Ubuntu Live CD to a USB drive and see if you can repair grub that way.

---

### Post by danbuter on 2009-03-11
It jumps straight to no OS, after showing the F9/F10 options. It then won't let me do anything. I have a flash drive plugged in, but it doesn't see it.

---

### Post by danbuter on 2009-03-11
Hmm, ok, now the BIOS just kicked in normally after I restarted 4 times. Thanks for the replies!

---

