---
title: "Hangs at boot -- caused by bad volume UUIDs in /etc/fstab?"
date: 2009-04-05
forum: General Help
---

### Post by Peasantoid on 2009-04-05
So I removed Hardy from /dev/sda3 (backing it up first; I've learned my lesson), formatted it as ext4, and installed Jaunty in its place. Then I realized I didn't like this new Ubuntu version and reinstalled Hardy from the backup, making sure that all permissions and whatnot were preserved. I used "sudo cp -axv ..." for those who are interested.

The problem is that the reinstalled Hardy no longer finishes booting. It hangs somewhere around where USB devices and SCSI stuff happens. I believe this has something to do with the UUIDs in /etc/fstab; when I installed Jaunty, the root partition /dev/sda3 and swap partition /dev/sda4 got reformatted. This would've changed the UUIDs (right?), so now the ones specified in /etc/fstab no longer correspond to anything.

How can I fix this gosh-darned frustrating issue? This has happened a number of times in the past, but I just figured it was because I botched something and then I did a reinstall. As you can imagine, I'd rather not have to go through the installation process again.

In short: What utility can be used to retrieve the UUID of a volume? Or do I not know what the hell I'm talking about and the problem is completely unrelated?

---

### Post by pbpersson on 2009-04-05
Did you re-format the partition as ext3 before putting Hardy back out there?

---

### Post by callie510 on 2009-04-05
The command "blkid" will list your partitions and their uuids. Try booting onto a live CD and running this in the terminal. You can then check out your fstab to see if this really is the problem.

I have had so trouble with UUIDs in the past. One time I copied a partition using Gparted and it duplicated the UUID - this caused me so much pain and anguish when the wrong partition got mounted until I figured out I had two partitions with the same UUID!! So I have edited my fstab to not use UUIDs anymore. It mounts with /dev/sda1, /dev/sda2, etc. I'm sure this is a terrible idea for lots of reasons, though, like the fact that I have had to edit my fstab by hand every time I mess with my partitions. But heck it works for me. Be warned.

---

### Post by Peasantoid on 2009-04-05
The UUID for /dev/sda3 did not match up (I used "sudo vol_id --uuid /dev/sda3"), so I replaced it. This had no effect.

@pbpersson: Probably, although since GParted sees ext4 as ext3 anyway, I'm not sure. Do you recommend deleting the partition and then creating a new one from scratch?
@callie510: So should I try using the device names instead of the UUIDs? This probably won't cause me much trouble since I'm only going to have the internal HD listed there anyway. What do you mean by "messing with partitions"? Do you need to re-edit fstab if you're just *resizing* them?

Something I forgot to add: With no external devices connected, the boot process hangs at the part about the "USB HID core driver".

---

### Post by pbpersson on 2009-04-05
> **Peasantoid said:**
> 

@pbpersson: Probably, although since GParted sees ext4 as ext3 anyway, I'm not sure. Do you recommend deleting the partition and then creating a new one from scratch?


Jaunty is the first version to support ext4, Hardy would not.  I don't know what would happen if you gave Hardy an ext4 partition to read data from.

---

### Post by Peasantoid on 2009-04-05
Changing the UUIDs to device names had no effect. I'm going to try erasing and recreating /dev/sda3 now.

---

### Post by Peasantoid on 2009-04-05
Well guess what? That did absolutely zilch! I am now royally f'n pissed!

I'm starting to think this has nothing to do with /etc/fstab. What other reasons could there be for this problem? Is my computer full of gremlins or something?

---

### Post by callie510 on 2009-04-05
:( Sorry, I have no idea. I recently restored my root and home partitions from a backup - although I used commercial imaging software, and I'm using 8.10 - and simply editing fstab & fixing grub has allowed me to boot fine. Someone else who knows more about the boot process and why it might be hanging there is going to have to help you.

---

### Post by Peasantoid on 2009-04-05
Maybe it could have something to do with external devices? I don't think copying would have preserved the contents of /dev. But this has worked before, so I have no idea.

---

### Post by Peasantoid on 2009-04-05
Just discovered that /boot/grub/menu.lst is using the old UUIDs. I'll update those and give it a try.

---

### Post by Peasantoid on 2009-04-05
RESOUNDING **SUCCESS**!!!!!!!!!!

Yeee-haaawww! Turns out GRUB was trying to boot from a nonexistent drive. So, for anyone in the future who has this problem, just remember to check /etc/fstab *and* /boot/grub/menu.lst. Anything that would have to reference disk volumes.

I am so happy right now. :)

---

