---
title: "Yet another problem with the Live CD"
date: 2006-09-03
forum: Desktop Environments
---

### Post by Rhapsody on 2006-09-03
Every time I try to do something with the Ubuntu Live CD, it seems totally unwilling to cooperate or make my life any easier whatsoever.

Now that I've made it mount my drives and resized my NTFS partition to make way for an ext3 partition that will one day carry its data, Ubuntu is refusing to let me write to it. I can read files on any drive and copy them, but I can only write them to my FAT32 partition. Ubuntu insists that I do not have permission to write to any of my ext3 partitions, even though I just created one of them with GParted in the last half hour.

So, how do I force the Ubuntu Live CD to give me permission to write to my own partitions? Suggestions would be welcome.

---

### Post by Rhapsody on 2006-09-04
Still haven't got this problem solved. I could just skip it and move on to installing Kubuntu, but then I'd lose all of my data, and I don't want to do that.

---

### Post by CatKiller on 2006-09-04
The problem is that you created the partitions as root (through GPartEd), but then when you browse the partitions with Nautilus, it's as a user. So the files are owned by root, and don't have write permissions for you. It doesn't matter for your FAT32 partition, since the filesystem just quietly ignores any permissions system.

Although I should advise you to use the terminal with the sudo command to chown (change the owner) to you, or chmod (change the mode) to give others permission, file permissions do my head in and I'd probably miss off an option. So instead, open a terminal and type ```
gksudo nautilus
``` Then find the folders that you want to write to, right-click->Properties->Permissions and either change the owner or change the permissions. Don't forget to close Nautilus when you're done, to save yourself doing something foolish with your elevated file browser.

If you don't mind me asking, why don't you install before it becomes a huge pain to do so, rather than a mild irritation? You could leave anything that you wanted to access after the install on the FAT32 partition, and performance is so much better when you aren't constrained by the read speed of the cd-rom drive.

---

### Post by Rhapsody on 2006-09-04
> **CatKiller said:**
> If you don't mind me asking, why don't you install before it becomes a huge pain to do so, rather than a mild irritation? You could leave anything that you wanted to access after the install on the FAT32 partition, and performance is so much better when you aren't constrained by the read speed of the cd-rom drive.
Because the current status of the disk is with a 50GB FAT32 partition, 5GB ext3 root partition, and 25GB ext3 /home partition. I want to change that to a 30GB ext3 root partition (I filled the last one, no chance of that with one that size) and a 50GB ext3 /home, but I there's still data on the 50GB FAT32 and 25GB ext3 /home that I want to keep.

My plan is to simply copy that data to my second drive (which will have a 248GB ext3 partition with 85GB of data on it once I'm done messing around with it) and peruse it at my leisure later. My new root and /home will start off completely new, giving me a fresh start.

---

### Post by CatKiller on 2006-09-05
> **Rhapsody said:**
> Because the current status of the disk is with a 50GB FAT32 partition, 5GB ext3 root partition, and 25GB ext3 /home partition. I want to change that to a 30GB ext3 root partition (I filled the last one, no chance of that with one that size) and a 50GB ext3 /home, but I there's still data on the 50GB FAT32 and 25GB ext3 /home that I want to keep.

My plan is to simply copy that data to my second drive (which will have a 248GB ext3 partition with 85GB of data on it once I'm done messing around with it) and peruse it at my leisure later. My new root and /home will start off completely new, giving me a fresh start.Fair enough. I'd suggest that you do it as soon as possible, though.

I've got a similar partition reshuffle coming up as I move Windows from a large drive to a small drive, and Ubuntu from the small drive to the large drive. I use Windows for two applications, so it probably doesn't need to be on an 80 Gig drive while Ubuntu is squeezed onto a 15 Gig one.

So did you get your permissions sorted out?

---

### Post by Rhapsody on 2006-09-06
> **CatKiller said:**
> So did you get your permissions sorted out?
Not entirely. I did enough to get my data backed-up and successfully reinstall, but I'm having further permissions problems now. Sure I'll get those sorted though.

---

### Post by CatKiller on 2006-09-08
> **Rhapsody said:**
> Not entirely. I did enough to get my data backed-up and successfully reinstall, but I'm having further permissions problems now. Sure I'll get those sorted though.

Good luck. The sudo nautilus command I suggested was before I noticed you're on kubuntu. I've not used it, but the appropriate command is ```
sudo <whatever the file manager in KDE is called>
``` That should give you a graphical interface with root privileges, so you should find it easy to change permissions and owners on any files or directories you fancy.

---

