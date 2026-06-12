---
title: "Best Downgrade Path"
date: 2008-12-11
forum: General Help
---

### Post by trentw2323 on 2008-12-11
Currently, Ubuntu is the only Operating System on my laptop. Unfortunately, there are a few apps that i need to run in a Windows environment an not in a virtual box. I have Ubuntu installed using the entire drive and finally have everything setup the way I like it. What is the best path to un-allocate part of my drive to use for Windows? I do have a network server so if it includes imaging this wont be a problem. Also, before i make any changes to the drive i want to make a full backup image of the drive just in case. What is the best software to use in Ubuntu to push a backup to a network location. Any help is greatly appreciated.

---

### Post by Locke_99GS on 2008-12-11
*rsync* to move the backup

*gparted* to resize partitions.

---

### Post by trentw2323 on 2008-12-11
> **Locke_99GS said:**
> *rsync* to move the backup

*gparted* to resize partitions.


I have been reading, and the part that i cannot wrap my mind around is which paths to backup and which paths to exclude. I think the difficulty i am having is there are so many ways to do things in Linux that work. I'm windows there is usually one way to do something and a thousand ways to mess it up. I just don't want to loose anything.

---

### Post by Locke_99GS on 2008-12-11
Well, to back up just the configuration and your personal stuff, back up /home and /etc, at the least.

Off the top of my head, resotring these folders (along with any packages you may have added - see *aptoncd* for that) on a fresh install should get you to how you were previously.

---

### Post by howefield on 2008-12-11
The complication with installing windows second is that it likes to think it is the only operating system on the machine so will wipe out your bootloader., you will need to reinstall grub otherwise you won't have Ubuntu.

The difficult (ie, longest) part of this is installing windows. So given that you have to do that anyway, I'd be tempted to save all my documents, maybe even the entire /home and install windows, giving it all the disk, set it up exactly as you want, download updates, defrag, ect then install Ubuntu and any extra packages you require, restore /home and finish by imaging the entire disk.

More than you need to do to achieve what you are after, but it is only what I'd do.

---

### Post by trentw2323 on 2008-12-11
> **howefield said:**
> The complication with installing windows second is that it likes to think it is the only operating system on the machine so will wipe out your bootloader., you will need to reinstall grub otherwise you won't have Ubuntu.

The difficult (ie, longest) part of this is installing windows. So given that you have to do that anyway, I'd be tempted to save all my documents, maybe even the entire /home and install windows, giving it all the disk, set it up exactly as you want, download updates, defrag, ect then install Ubuntu and any extra packages you require, restore /home and finish by imaging the entire disk.

More than you need to do to achieve what you are after, but it is only what I'd do.

Thanks to everyone, and to the reminder about GRUB. Sometimes I can get GRUB to reinstall properly and other times i cant. Thanks for the advice.

---

