---
title: "Install FIZZLE"
date: 2006-09-03
forum: Desktop Environments
---

### Post by RKelly5327 on 2006-09-03
Hi folks,
I tried to install Ubuntu (latest version) last night from a CD I made from the ISO image file I downloaded, onto a 250G Western Digital drive which already has XP Pro on it. The CD booted fine and up pops the desktop. The fizzle happened when I told it to install. WOW! There is no progress graph to let you know how things are going- at least one never came up if there really is one, so I had no clue as to how it was going. When it first started to install it defaulted to 50% of the drive which wouldn't work so I went for 35%. That amounted to about 80Gs. I started the install around 6:00 PM last night. The little hour glass that MS uses has been replaced by that little circle thing that goes around and around. It kept going around and around all night long and was still doing so at 9:30 this morning! It never did install. Anyone have any ideas why the fizzle?
Thanks to all, Hope I can get this solved. Program looks great!
Ron K.

---

### Post by meng on 2006-09-03
Possibilities I can think of:
corrupted ISO download or CD burn
some idiosyncracy with the desktop/liveCD and your system

You could try one of the following
check md5sum of the ISO
reburn at lower speed
download and burn the alternate CD (no live desktop; text-based installer)

In my experience, an Ubuntu install takes 20-30 minutes. Obviously mileage may vary depending on system specs, but there's no need to wait longer than an hour - if it's hung, it's hung.

---

### Post by RKelly5327 on 2006-09-03
I'll check into those things and see what happens.
thanks,
rk

---

### Post by RKelly5327 on 2006-09-03
Boy! Been having a nightmare trying to get to these pages! The server must be choking! I ran the check on the CD and it checks out fine. I can reburn it at a lower speed if that would help. Don't know. I did try to install it again and tried the format manually so I could see what was going on. I set the space I wanted to save for Ubuntu and hit the go get 'em button and it froze right up. The whole drive is already formatted NTFS for XP. Would it help to partition it off and format the partition ahead of time? What file system would I use if I did that? Also, I don't know where to download the text-based installer? I didn't know there was one. Where do I find that? What happens with that? Do you get text messages that tell you what to do next??
Thanks again. Hope I can get back on the board to get the answers.
Ron

---

### Post by meng on 2006-09-03
You don't need to partition the drive in advance, but it will help if you defrag the Windows drive first. The filesystem you need for Linux is pretty much anything except NTFS. If you go to [www.ubuntu.com](www.ubuntu.com) and downloads, you'll have the option for desktop CD and alternate CD versions. The text-installer has the same steps as the GUI-installer.

---

### Post by RKelly5327 on 2006-09-03
I have Diskeeper 10 running all the time so it's well defragged. I'll try the alternate and see how that goes. Better, I hope!
Thanks again.
Ron

---

### Post by RKelly5327 on 2006-09-04
The latest-
I downloaded the alternate text version mentioned, ran that, got to the same place and it failed. It did not freeze like the Live CD, but the problem is that it acts as if the drive cannot be accessed to resize the partition and set up a new partition! I even tried it from XP with Partition Magic 8 and it also failed. First I tried having it resize the original partition, set up the new one and format it to FAT32. The whole thing failed. Then I tried simply resizing the original partition and not doing anything to the new partition, just left it blank. It too failed. I can see it fail by the errors posted by PQ 8 during the reboot process. How in the world is it possible that the drive can be prevented from being resized??? Any ideas on that?? Doggone, I really want to try this Ubuntu thing...
Thanks,
Ron K.

---

### Post by meng on 2006-09-04
Ron
I feel your pain, and you aren't alone. This whole weekend there have been a rash of complaints about similar problems, even with using Partition Magic beforehand (in fact, I think this tends to cause more confusion for the installer!). I must have been lucky that I didn't come across such problems. It makes me wonder in what way the installer (and the partitioner that comes with it) is not quite up to scratch.
P.S. I'm sure the problems haven't been limited to this weekend, it's just that I've been spending a lot of time browsing the forums this weekend!

---

### Post by RKelly5327 on 2006-09-04
Linux for cows!!! Maybe that's the problem. Ha. You feel my pain? I have a broken foot. Which of your feet hurt? :D  U could be right about something amiss with the installer, but that doesn't explain why Partition Magic can't even resize the drive. I've used PQ a lot and never ran into that before. Really is confusing. What to do next?
rk

---

### Post by RKelly5327 on 2006-09-04
I found the problem, Gang. There was an error in the file system somewhere. I ran chkdsk /f and it fixed the thing, rebooted onto the Ubuntu CD and it re-partitioned, resized, and loaded everything just fine. I did try following instructions on loading GRUB elsewhere besides the MBR (I used /dev/hda2). When I rebooted it was supposed to go directly to the XP thing, then I was supposed to boot from the Ubuntu Live CD, mount the NTFS partition, do some commands and edit the boot.ini file in XP, but a menu came up anyway. So far I've been able to boot into both systems.

If anyone else says they can't resize/repartition, have them to be sure to run chkdsk /f besides defragging.

Thanks to everyone. It's almost overwhelming to be a lowly newbie, not even know what to look for or where to look, but not have a clue what all these new terms mean. We'll see where it all leads.

Thanks again.

Ron K

---

### Post by Tommytrojan on 2006-09-04
Ron,

I'm having a similar problem with the installer. When I double-click on Install nothing happens. I tried several times rebooting from the LiveCD and clicking Install. I haven't even gotten a menu or window to select an installation drive or anything. I'll go and check my download. Once I get to the point where I can choose an installation partition I want to install to a USB drive, are there more problems to be expected?

Cheers,
  Tommy

---

