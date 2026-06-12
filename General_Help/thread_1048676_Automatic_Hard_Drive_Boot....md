---
title: "Automatic Hard Drive Boot..."
date: 2009-01-23
forum: General Help
---

### Post by Roasted on 2009-01-23
Random question...

Say I have 4 drives in my computer. 1 has the operating systems. If I have all 4 plugged in when I do my initial install, format each one to EXT3, can I set each one a mount point there so they get entered into fstab so each time I boot up the PC all 4 of them boot automatically?

I've always just hit blkid and gotten the UUID of each drive and added them to fstab on my own. I wasn't sure if doing this during the install would enter these drives into fstab on their own.

---

### Post by Roasted on 2009-01-28
Nobody??

---

### Post by taurus on 2009-01-28
> **Roasted said:**
> Random question...

Say I have 4 drives in my computer. 1 has the operating systems. If I have all 4 plugged in when I do my initial install, format each one to EXT3, can I set each one a mount point there so they get entered into fstab so each time I boot up the PC all _**4 of them boot automatically**_?

I've always just hit blkid and gotten the UUID of each drive and added them to fstab on my own. I wasn't sure if doing this during the install would enter these drives into fstab on their own.

I think you mean those 4 drives will mount automatically (not boot) each time you boot Ubuntu.  The answer is yes.  Just have an entry for each drive with a unique mount point in /etc/fstab.

---

### Post by DGortze380 on 2009-01-28
> **Roasted said:**
> Random question...

Say I have 4 drives in my computer. 1 has the operating systems. If I have all 4 plugged in when I do my initial install, format each one to EXT3, can I set each one a mount point there so they get entered into fstab so each time I boot up the PC all 4 of them boot automatically?

I've always just hit blkid and gotten the UUID of each drive and added them to fstab on my own. I wasn't sure if doing this during the install would enter these drives into fstab on their own.

You're post is a bit confusing... I think what you want to do is set mount points for 4 different drives during the initial install.

Yes, you can do this. For example, partition your first drive with root (/) and swap. Partition the other 3 as 1 partition each ext3.

So it would look something like this??

sda0  /
sda1  swap
sdb0  /home
sdc0  /usr
sdd0  /someOtherDir

---

### Post by Roasted on 2009-01-28
> **DGortze380 said:**
> You're post is a bit confusing... I think what you want to do is set mount points for 4 different drives during the initial install.

Yes, you can do this. For example, partition your first drive with root (/) and swap. Partition the other 3 as 1 partition each ext3.

So it would look something like this??

sda0  /
sda1  swap
sdb0  /home
sdc0  /usr
sdd0  /someOtherDir

yeahhh. Exactly. See when I did my computer, I ran the install with 1 drive. But I added 3 SATA drives to it since then. I knew how to do it manually with blkid and editing the /etc/fstab file, but I wasn't sure if that would be an automated task if I had all 4 drives in the computer when I ran the install originally.

Thanks!

---

### Post by Roasted on 2009-01-30
Okay, question here...

As I said, I have 4 drives. 1 for Vista/Ubuntu... and the other 3 which are simply backup drives, each containing a single EXT3 partition that takes up the entire drive. 

I had all 4 SATA drives plugged in and I reinstalled Ubuntu. The other 3 drives I mounted to their designated shares.

sdb1 to /media/localbackup
sdc1 to /media/storage
sdd1 to /media/storagebackup

When I booted up, the boot seemed to hang like no other. It was unreal. Finally I powered down, unplugged the other 3 drives, and kept my main drive plugged in. 

I ran the install as normal, only having my main drive plugged in. Afterwards, I powered down and plugged in my other 3 drives. I booted up just fine, seeing as though my single drive I had plugged in earlier took over the SATA boot disk priority and was set to "master", if you will. Afterwards, I just edited /etc/fstab to put in the UUID of my other 3 drives. So now, all 3 backup drives automatically boot up and are mounted when I log into Ubuntu.

My question is, why in the world did I need to unplug my other drives to install Ubuntu on the single? Has anybody else had to do that? I just don't understand why 1 drive makes things work while 4 drives just gives me a headache. 

Each time I do a fresh install of my entire system, I'm always thinking, naw, I don't need to install on a single drive and unplug the others. Yet I run into issues, and the easiest solution is just to use a single drive.

Does anybody else do this?

---

