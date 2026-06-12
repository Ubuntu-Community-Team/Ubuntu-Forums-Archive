---
title: "preinstallation decisions"
date: 2010-12-30
forum: Desktop Environments
---

### Post by ppm123 on 2010-12-30
i have dual core processor, 2gb ram --and win7 installed. 
i am planning to dual boot with ubuntu 
need following doubts cleared. 
1) for a individual user -is there any difference between long time support and any other version? i have ubuntu 10.10 live cd with me. 
2)for the installation -which is better ext4 or ext3?
3) can read and write to ntfs paratiion?using ntfs-3g driver? and can it be the same partion shared with win7 for data?
4) is it better to keep os install separate, so if required, os reload can be done comfortably?in that case how many partitions shold i make for the install ?
5) while using gparted live, is possible to use the screen shot button ?if i do not have linux installed and running only windows?if yes, then where should i look for the saved image?
--ppm123

---

### Post by SnickerSnack on 2010-12-31
Welcome to the forum!

1. 10.10 is newer, has more/better features, and should have more things working correctly than 10.04.  It may be that over then next year or so, 10.04 will have fewer bugs in it, being that it is LTS.  However, I've found that if you want to tweak your system much, you're going to run into problems that can be easily fixed by updating certain pieces of software beyond what is the default for 10.04.  I would always recommend using the latest version.

2. I'm no expert, but I doubt there's any noticeable difference for the non-expert user.

3. I know that writing is possible, though I don't know how easy or reliable it is.  I have no trouble reading my ntfs drives, though I don't think I've ever tried to write to them.

4. Yes, I think it is *very* important to keep the root filesystem and the home directory on separate partitions.  Two partitions should be fine.  In the past, when I set up a desktop, I also had a separate partition for /var as that's where logs are stored.  Right now, I have one NTFS partition for windows, one FAT partition as a shared drive between the two, 3 15 GB EXT3 partitions to hold linux installations and one largish EXT3 partition to hold the shared /home directory.  The reason I have 3 smallish EXT3 partitions is that I wasn't sure what flavor of linux I wanted to use.  Right now, I have Ubuntu 9.10 32-bit, Xubuntu 10.10 64-bit, and a blank 15 gig partition.  I've been thinking of putting something new on the blank partition, but it's time consuming for me to get a new install up and running since I'm using very non-standard hardware.

5. I would guess no on that.

---

### Post by nebileix on 2010-12-31
> **ppm123 said:**
> i have dual core processor, 2gb ram --and win7 installed. 
i am planning to dual boot with ubuntu 
need following doubts cleared. 
1) for a individual user -is there any difference between long time support and any other version? i have ubuntu 10.10 live cd with me. 
2)for the installation -which is better ext4 or ext3?
3) can read and write to ntfs paratiion?using ntfs-3g driver? and can it be the same partion shared with win7 for data?
4) is it better to keep os install separate, so if required, os reload can be done comfortably?in that case how many partitions shold i make for the install ?
5) while using gparted live, is possible to use the screen shot button ?if i do not have linux installed and running only windows?if yes, then where should i look for the saved image?
--ppm123

Try wubi instead and get used to ubuntu first before you make any major changes to ur harddisk.

---

### Post by ppm123 on 2010-12-31
thanks for the reply, helped me to clear my doubts, will post again after installation-ppm123

---

