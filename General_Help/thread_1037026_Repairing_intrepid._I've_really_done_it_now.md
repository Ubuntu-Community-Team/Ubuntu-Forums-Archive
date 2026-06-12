---
title: "Repairing intrepid. I've really done it now"
date: 2009-01-11
forum: General Help
---

### Post by brawnyman713 on 2009-01-11
Ok, the irony is I did this while trying to create a backup of my hard drive. So I installed imagepart and I was going to use that to back up my linux install (/dev/sda2). I had a backup drive plugged in and everything. Here's the problem. Because the external drive I had was NTFS (I think this is the reason, not totally sure), imagepart couldn't write to it. So I just let it create the file wherever it was gonna create it. Since I was using a liveCD (Sidux 2008-03, I knew it had all the tools I needed so that's what I used) that directory was my 2 gig swap partition. Problem is that my ubuntu install, with all the programs I have and a small amount of media totalled to around 22 gigs. Obviously wouldn't fit. Rather then formatting my external to something that could still be written to with imagepart and still be read by windows (fat, maybe?), I had the brilliant idea to unmount my swap and resize my windows and linux partitions to make some room for this 20 gig file, which is record breaking on the stupid scale now that I've had time to reflect on it. The worst part is that GParted EVEN WARNS ME TO BACK UP MY CRITICAL DATA, but do I listen? No. I can just use the backup I'm going to create once I have the room on the swap, right? Wrong. So I know that sometimes the resize can take a while (this is late at night) so I leave my box running and go to bed. I wake up and GParted has frozen on the first step. I was starting to get an idea of just how stupid of a move I'd made at this point. So I restart my computer, but it doesn't like to let me open the CD drive before it tries to boot off of it. No problem. Just set hard drive to boot first. Then I boot up and it tells me that there was a problem with my config so it can't boot into a GUI. Ok, a little annoying, but I know my way around the command line fairly well. I'll just copy my home directory and these PHP scripts that I'd just spent 50 hours coding for my parents onto my external and do a fresh install of ubuntu. It seems that /var/www/ is still intact. Ok. I'll just take my flash drive, mount it, and then just move the files onto that. The rest of the stuff is valuable, but not critical. I plug in the flash drive, and it's in /dev/sdc1. Ok. Not happening. Everything in dev is printed in orange, and a -l modification to my ls command reveals that the permissions are preceded by a b, which I can only assume means broken. When I try to create the folder (with sudo) /backup, it tells me it's a 'read-only file system'. Obviously I've really screwed myself over. So I can't mount my flash drive and I can't just write the contents that I want to /dev/sdc1 because it tells me everything is read-only. What do I do? I desperately need these files, and quickly.

---

### Post by brawnyman713 on 2009-01-11
I know this is really over the top stupid, and I'm sorry about it. I should've known better. I really need these scripts. I can read them, but I can't mount any storage that I can put them on

---

### Post by linfidel on 2009-01-11
As a quick fix that shouldn't do more harm, can't you boot from a live CD, and access the needed partitions on that system, mount your flash drive, and copy to it?

Then, maybe fix the problem using the live CD.

---

### Post by cariboo on 2009-01-11
You didn't specify if you had a laptop, or a desktop computer, but if you have a desktop computer, you can manually open the cdrom drive and insert a LiveCD.

To manually open the cdrom drive look for a small hole on the front of the drive, straighten a paper clip and insert it in the hole and gently push it in, this should contact part of the eject mechanism and open the tray. You should now be able to boot from a LiveCD and mount you external drive and copy your files to it.

Jim

---

### Post by linfidel on 2009-01-11
I think his problem was that he was booting from the CD, so he was unable to eject it easily because it was being used.  You don't get much time to eject it before booting.  I've had that happen, but I just press delete to enter the BIOS screen, then eject the CD and reboot.  

> **cariboo907 said:**
> You didn't specify if you had a laptop, or a desktop computer, but if you have a desktop computer, you can manually open the cdrom drive and insert a LiveCD.

To manually open the cdrom drive look for a small hole on the front of the drive, straighten a paper clip and insert it in the hole and gently push it in, this should contact part of the eject mechanism and open the tray. You should now be able to boot from a LiveCD and mount you external drive and copy your files to it.

Jim

---

