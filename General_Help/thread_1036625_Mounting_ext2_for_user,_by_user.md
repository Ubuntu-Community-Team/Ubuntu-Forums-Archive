---
title: "Mounting ext2 for user, by user"
date: 2009-01-11
forum: General Help
---

### Post by jeenuv on 2009-01-11
Hi,

I had an NTFS USB HDD which I just formatted as ext2. But when I plug it in, the disk is getting mounted on a directory with ownership and group set as root. Hence it's not writable for me (I do have the root privileges though).

This is what I have in /etc/fstab:

LABEL=Jeenu-Disk /media/Jeenu-Disk ext2 user,rw,exec,async,auto 0 0

I'm able to mount it manually by 'mount -L Jeenu-Disk' (without sudo). I also tried creating /media/Jeenu-Disk with user and group set to mine. Even then they're changed to that of root's on mount, and reverted back to mine when unmounted.

I tried adding myself to the group disk (which is the group of device file /dev/sdc1), and later changed 'user' to 'group' in fstab. But again the same thing happens. I know there's a 'umask' option to vfat file systems. But I couldn't find anything similar for ext2.

All I wanted is to mount the disk as and writable to the ordinary user 'jeenu'.
Please help.

:J

---

### Post by mikewhatever on 2009-01-11
Try the following (assuming Jeenu is your username):
sudo chown -R Jeenu:Jeenu /media/Jeenu-Disk
sudo chmod -R 755 /media/Jeenu-Disk

It also looks like the partition identifier is missing from the fstab line.

**/dev/sdc1** LABEL=Jeenu-Disk /media/Jeenu-Disk ext2 user,rw,exec,async,auto 0 0

---

### Post by kerry_s on 2009-01-11
when i have problems like that i use pmount.

sudo apt-get install pmount
sudo umount /your/device
pmount /your/device

to unmount:
pumount /your/device

this:
LABEL=Jeenu-Disk /media/Jeenu-Disk ext2 user,rw,exec,async,auto 0 0

should be:
LABEL=Jeenu-Disk /media/Jeenu-Disk ext2 **users**,rw,exec,async,auto 0 0

---

### Post by portfot on 2009-01-11
[img]http://www.top1gaming.com/cosplay2/20081105/RowdyReiko-1.jpg[/img] See the answer [[color=#800080]click here[/color]](http://www.top1gaming.com/coscontent-172.html).  Want to see [[color=#800080]more pics[/color]](http://www.top1gaming.com/cosplayer.php)? Show yourself  on our forum [[color=#800080]click here [/color]](http://www.top1gaming.com/forum/index.php?gid=27)**Recommend:**[[color=orange]Sexy Halloween Cosplay[/color]](http://www.top1gaming.com/coscontent-169.html)[[color=orange]Seung Mina from Soul Calibur 2[/color]](http://www.top1gaming.com/coscontent-158.html)

---

### Post by jeenuv on 2009-01-11
> Try the following (assuming Jeenu is your username):
sudo chown -R Jeenu:Jeenu /media/Jeenu-Disk
sudo chmod -R 755 /media/Jeenu-Disk

It also looks like the partition identifier is missing from the fstab line.
This is what I finally did. Thanks.
> /dev/sdc1 LABEL=Jeenu-Disk /media/Jeenu-Disk ext2 user,rw,exec,async,auto 0 0 
Partition identifier wasn't necessary for me; I was able to get away without that. In fact there were other entries without that. More over, I think, LABEL's are used to obviate partition identifies.
> sudo apt-get install pmount
sudo umount /your/device
pmount /your/device
pmount was useful; thanks!
> LABEL=Jeenu-Disk /media/Jeenu-Disk ext2 users,rw,exec,async,auto 0 0 
The mount(8 ) manual says users is required only if any user were able to unmount the drive. So user is enough for me.

Thank you all.

---

