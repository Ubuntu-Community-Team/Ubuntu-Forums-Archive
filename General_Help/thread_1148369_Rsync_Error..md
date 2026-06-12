---
title: "Rsync Error."
date: 2009-05-04
forum: General Help
---

### Post by Roasted on 2009-05-04
For months now I have ran an rsync script with the use of crontab to synchronize all of my data to other hard drives in my system. Last night when I was redoing my brothers computer I ran the script manually by simply executing it in terminal. I got some errors, regarding failed to set times....

The error was:


sending incremental file list
pam/
rsync: failed to set times on "/media/storagebackup/pam": Operation not permitted (1)


This worked fine before. Why doesn't it work now?

Here's my script:


#!/bin/bash
rsync -a --progress --delete --exclude=.gvfs /home/jason/ /media/localbackup/
rsync -a --progress --delete --exclude=.gvfs /media/storage/ /media/storagebackup

4 SATA drives. A's home directory gets copied to B, and C's contents gets copied to D. Make sense?

---

### Post by StuartN on 2009-05-04
> **Roasted said:**
> This worked fine before. Why doesn't it work now?

For some reason you don't have ownership of the two mount-points. If you run "mount" and look at /media/localbackup/ and /media/storagebackup you will probably not see "user=Roasted".

Mounting with the option "uid=Ubuntu-username" should get rid of the error. I have no idea why it worked before and doesn't work now.

---

### Post by Roasted on 2009-05-04
All 3 drives mount by UUID upon system startup in fstab.

I've had this setup for a long time, so I have no idea what recently changed to cause these issues.

I like running the script as a non-root user (myself) because then things run the way I want. Check this...

/media/storage is the mount point for my one drive via UUID in fstab. /media/storage is owned by root when it is not mounted, however it is owned by jason when mounted. Why is this good? If the drive dies and gets unmounted and I run the script, that way it doesn't run the script since I'm not a root user. If I run the script as root, and the /media/storage drive is not existent, it pushes the data to my root partition. Naturally if you push 200gb of data on a 25gb root partition, it'll max out - therefore my system will be nothing more than a severe headache to fix - requiring me to boot to a LiveCD and delete the data that got pushed to the root partition. I know - I've had this happen.

So it's nice having the mount points owned by myself (Jason) so I can run the script with no root access.

I'll check the permissions when I get home... I can't remember if I checked them last night, cause if I did I certainly forgot what they are.

---

### Post by Roasted on 2009-05-04
Does it matter if I use sudo or not?

jason:jason owns the backup script. So I would execute it while logged in as myself (jason) by simply running "backup". Crontab is set up to run it as the user jason twice a day.

When I use sudo backup, I don't get the error. When I use backup, I get the error, but I'm not sure how it worked before or if I just didn't notice.

I REALLY want to use it without root though, because if a hard drive dies and unmounts itself, I don't want the script to run with root priviledges. If it does, that means I'll be rsyncing to my root directory if a drive goes down, since the folders unmounted are owned by root and mounted are owned by jason.

EDIT - Just found this.

[http://ubuntuforums.org/archive/index.php/t-163110.html](http://ubuntuforums.org/archive/index.php/t-163110.html)

"Just noticed that in order to correctly run remote rsync backups using the archive (-a) option, which preserves ownerships and permissions, you need to run as root on the target machine. I don't know of a way to get rsync to sudo on the target... does anyone else?"

bingo. rsync -a. That's what I run.

That thread is dated 2006. Is it still the same?

---

### Post by Roasted on 2009-05-04
All right... I've done some digging.

Guys, what do you suggest I do here?

rsync -a gives me everything that I want. However, running that requires root. But my data is stored on /media/storage. /media/storage is owned by jason when mounted, and root when unmounted. So that way if I run the rsync script WITHOUT root, if the drive has failed and is not mounted properly, the script will fail due to jason not being able to write to a root directory.

BUT... I need to be root to use the rsync -a function...

Is there ANYTHING I can do to get around this issue?

EDIT - Yeah... it is what it is. -a stands for several switches in one... one of them being -o, which retains the ownership of the folder... in order for -o to run, it needs root permissions. Because -a also includes -o in the mix, -a needs root permissions.

To get around it, instead of running rsync -a, I ran rsync -r -p -g.... which is -r recursive, -p permissions, to keep the permissions on all of the files (which doesn't require root permissions because I'm part of the group that owns the files), and -g to retain group permissions, which also doesn't require root permissions because I'm part of the group that owns the file. If I wasn't a member of that group, I'd error out here too... but for what I'm doing, only -o is the curve ball.

---

### Post by Roasted on 2009-05-06
So finally, I got smart. I don't know why I didn't think of this originally.

Ignore what I said earlier and just focus on this here... Reason I'm doing this is for future reference in case anybody stumbles across the same issue I had.

I have two drives in my computer specifically for Samba usage. All computers in the house back up to my computer at 3 am. Then at 330 am (giving enough time for the backup to be completed) the drives synchronize so I have 2 copies of backups of the data that was just pushed to my computer. With that, I used rsync, which is where I ran into this issue.

I had the individual shares owned by the user themselves, and just added myself to the group with 775 rights so I was able to access the files if need be since I was part of the group. But then I thought about work with how we handle groups and whatnot and it hit me. I was doing things backwards.

This is my computer. It's my setup. Therefore, (now) I own the folders. So I changed ownership of every share to me (jason) and added all of the samba users to the "sambashare" group. I kept the 775 octal rights to the shares too... meaning sambashare had full rights to the folders, so the samba users being a member of that group were able to get to their shares and read/write accordingly.

Additionally, because I have password protected accounts on each share, even though all of the users belong to 1 universal group (theoritically meaning fred COULD read/write to bob's share) they ultimately can't do this due to the restricted permission from samba itself.

Each user has an account.
Each user is part of the same group.
Each user must log in to access the share.

Therefore users can open the door to their share and their share only.

Ultimately:

When Fred synchronizes to his share, he owns the data because he's logged in when the data is written. But I own the share itself that he backs up to, so I can run rsync -a without root permission because the share is owned by me. So when I run sudo rsync -a and the data gets pushed to my backup drive, fred's ownership stays with the files themselves. If I run rsync -a as I will be, fred doesn't stick as the owner - the owner gets tagged as myself (jason). However, fred will has full access to the files because he's part of the sambashare group which has full access. And even when Fred syncs his data to my drive and he's tagged as the owner, if need be, I can still manipulate it the way I need to because I'm a member of the sambashare group. But ultimately all I need to get my non-root script done with is to be the owner of the share fred is backing up to (which I am) and have sambashare as the group with fred as a member so he can have access to it (which he does).

Even still, this works out perfectly.

Win.

---

