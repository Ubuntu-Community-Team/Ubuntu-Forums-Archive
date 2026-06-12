---
title: "Unable to change file permissions"
date: 2010-12-04
forum: Desktop Environments
---

### Post by jascayne on 2010-12-04
I recently did a fresh install of Ubuntu Maverick, and have found a slight issue with file permissions. Before starting the installation I backed up all my files to an ext3 partition, then during the process I moved all of these files over to an NTFS partition that I am using as a joint storage location for both Ubuntu 10.10 and Windows 7. Upon booting into my fresh Maverick install I found that all the files on my NTFS partition are now owned by root and I am unable to change the permissions using the conventional methods I am used to. I have tried using the GUI method through the properties of the folder, I've also tried using chown and chmod, but all to no avail... No matter how I make the change to the permissions, it will always revert back to root within seconds. Any advice for someone who desperately wants full read/write access back to their data?

---

### Post by endotherm on 2010-12-04
ntfs doesn't do ownership the same way unix does, so its a little differant. do you have ntfs-3g and ntfs-config installed?

---

### Post by jascayne on 2010-12-04
To your first response, I wouldn't dream of running commands like that without sudo, don't worry ;). To the second, Ubuntu installed ntfs-3g, but not ntfs-config so I've installed that and am going to give it another run. I'll post back when I find out if it works or not.

edit: I just ran sudo ntfs-config and it immediately complained about not being able to find HAL... I vaguely remembered that Ubuntu switched from HAL to Dbus (I believe?) a couple versions ago and checked /etc for a hal directory and lo and behold, found nothing. Would simply installing HAL fix this issue maybe if ntfs-config is looking for it instead of Dbus?

---

### Post by endotherm on 2010-12-04
do you own the mount folder? I never really have any trouble with it, but I do try to avoid doing too much with ntfs on ubuntu.

---

### Post by jascayne on 2010-12-04
I'm mounting the ntfs partition as /storage on ubuntu, then linking to it from my home folder to essentially use it as a data partition that I can see from either OS without needing to constantly reboot my machine just to move files over to 7 since I have had constant trouble trying to get ext partitions to read in windows. Root owns /storage and plugdev is the group that has ownership over it. All files and folders contained within have the same permissions attached to them. Kinda stumped...

---

### Post by endotherm on 2010-12-04
> **jascayne said:**
> I'm mounting the ntfs partition as /storage on ubuntu, then linking to it from my home folder to essentially use it as a data partition that I can see from either OS without needing to constantly reboot my machine just to move files over to 7 since I have had constant trouble trying to get ext partitions to read in windows. Root owns /storage and plugdev is the group that has ownership over it. All files and folders contained within have the same permissions attached to them. Kinda stumped...

well, are you a member of the plugdev group? try chowning the /storage to be owned by <youruser>:root and that shoudl propagate to the files inside. links don't change permissions, so owning the link doesn't do much in and of itself.

---

### Post by jascayne on 2010-12-04
Yeah I'm a member of plugdev already, apparently Ubuntu was kind enough to do that one for me... I tried your suggestion and it still won't take any changes... I'm hoping I don't have to try and wiggle stuff around and reformat it from ntfs to something else... I have almost no free space to be able to play that game, and I have a few files over 4GB that I cannot store on a fat32 partition, so I'm kind of stuck on how to keep my data in sync between both operating systems without having to transfer files back and forth between different partitions.

---

### Post by endotherm on 2010-12-04
I'm sure there is a better option available. as I said, ntfs usually jsut works for me. 
try creating a new folder in /media take ownership of it, and mount your drive there. if it fails, send back a ls -l of both media and your mount dir, as well as the output of 'mount'.

---

### Post by jascayne on 2010-12-04
Don't get me wrong, NTFS support seems to be working. Kind of... The main thing that made me notice the issue is that when Dropbox tried to sync for the first time after installing, it cranked back a ton of errors about not having permission to do things, so I checked it out and I cannot delete anything, which I'm guessing would explain Dropbox's complaints. i'm going to keep trying a couple other ideas I've got kicking around in my head, but I'm not exactly hopeful about using a live usb stick to try and forcibly change the permissions around

---

### Post by jascayne on 2010-12-05
Still haven't been able to get this fixed... I tried making a folder in /media and taking permission of it like you had suggested, and I couldn't take permission over the folder, even when I drop to root and try punching everything in from a psuedo terminal (I can't remember the proper name for when you hit CTRL+ALT+F1) and it still won't accept the permission change.


edit: cayne@hq:~$ ls -l /media/
total 0
cayne@hq:~$ ls -l /storage/
total 24
drwxrwx--- 1 root plugdev    0 2010-12-04 23:03 android-sdk-linux_x86
drwxrwx--- 1 root plugdev 4096 2010-12-04 23:03 Desktop
drwxrwx--- 1 root plugdev    0 2010-12-03 19:55 Documents
drwxrwx--- 1 root plugdev    0 2010-12-04 23:03 Downloads
drwxrwx--- 1 root plugdev 4096 2010-12-04 16:15 Dropbox
drwxrwx--- 1 root plugdev 4096 2010-12-03 20:04 Installers
drwxrwx--- 1 root plugdev    0 2010-12-04 09:26 ISO
drwxrwx--- 1 root plugdev 8192 2010-12-03 20:12 Music
drwxrwx--- 1 root plugdev    0 2010-11-27 20:18 Pictures
drwxrwx--- 1 root plugdev 4096 2010-12-03 20:31 Videos


cayne@hq:~$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda2 on /boot type ext2 (rw)
/dev/sda1 on /storage type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3 on /windows type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/cayne/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cayne)

---

### Post by holiday on 2010-12-05
I had a problem like this that turned out to be about how NTFS uses uids not usernames. So Bob 1001 on one side is not the same Bob as Bob 1002 on the other, whereas Jill 1001 on one side is the same as Bob 1001 on the other.

And root on your system doesn't give you root on the network drive. That's actually a good thing. You don't want to give everyone mounting a NTFS drive to have root access to the network. 

NTFS is troublesome. Most people use Samba. It's easier that NTFS, and Ubuntu supports Samba well.

---

### Post by endotherm on 2010-12-05
ok, first off, try chowning /storage to <youruser>:root. it is my understanding that NTFS permissions are directly applied from their mountpoint. 

I also recomend mounting it in /media/storage rather than /storage. I've heard in past that /media is special.

---

### Post by Morbius1 on 2010-12-05
Getting a little lost here. From this:
> cayne@hq:~$ ls -l /storage/
total 24
drwxrwx--- 1 root plugdev    0 2010-12-04 23:03 android-sdk-linux_x86
drwxrwx--- 1 root plugdev 4096 2010-12-04 23:03 Desktop
drwxrwx--- 1 root plugdev    0 2010-12-03 19:55 DocumentsIt looks like you have an entry in fstab that looks something like this:
> /dev/sda1 /storage ntfs defaults,umask=007,gid=46 0 0Since you are a member of plugdev by default you should have full read / write access to the contents of /storage.

If for some reason you need to take possessions of the partition then you can't chown ( or chmod either ) a windows filesystem because there is nothing to chown. Instead you will need to change the mount parameters in fstab to this:
```
/dev/sda1 /storage ntfs defaults,umask=007,uid=1000,gid=46 0 0
```uid=1000 will make you the owner.

Remember: Ownership/permissions on Linux filesystems are done after a mount. For Windows filesystems it's done at the moment of mount.

Have I misunderstood the nature of the problem?

---

### Post by asmoore82 on 2010-12-05
[SIZE="3"]+1[/SIZE] for check your fstab.

On a modern Linux like Ubuntu, I would skip fstab altogether and mount from nautilus.

---

### Post by jascayne on 2011-07-06
I know this has been dead for a while now, but i just finally logged back into this site after months, and I checked out my subscribed folders, saw this and just thought I would update:

I've got everything working perfectly now. I've played around with a few different things, and what seems to have worked thus far (I am pretty certain I can say it is relatively foolproof, this method has worked on a handful of different distributions for me since I worked it out) is to edit the fstab. Best way I have found to edit it is to change the mount as follows:

```
UUID=281EABCB3C055536 /storage   ntfs    defaults,umask=007,gid=46 0 0
```

By using the UUID of the partition, you will be far less likely to have problems in the future if partitions get rearranged for some reason. You by no means *need* to use the proper identifier for the disk, but it is a safer way to go. When mounting with /dev/sdXY, if your partitions get shuffled around in some way and their order changes, you might end up with some rather odd results... (Trust me, I definitely needed a live cd to get that mess fixed when it was trying to mount all my partitions with the wrong file systems, wrong locatations, etc.)

---

