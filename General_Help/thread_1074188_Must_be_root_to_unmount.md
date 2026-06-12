---
title: "Must be root to unmount"
date: 2009-02-18
forum: General Help
---

### Post by xjgnsdof on 2009-02-18
I have two NTFS partitions that I automount through the ntfs-3g app. When I click on the eject button next to either partition's name, I get the following message: "You are not privileged to unmount the volume ________." Later, a window pops up saying: ```
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

I then have to execute "sudo umount /dev/sda1" to unmount that volume. How do I set it so I can mount and unmount my NTFS partitions just by clicking a button?

---

### Post by mtopro on 2009-02-18
> **elgilicious said:**
> I have two NTFS partitions that I automount through the ntfs-3g app...

I then have to execute "sudo umount /dev/sda1" to unmount that volume. How do I set it so I can mount and unmount my NTFS partitions just by clicking a button?


I am not familiar with the ntfs-3g gui app, but it sounds like you must unmount as root?  This would make sense.

Can modify your shortcut to open the app or button you use to eject the partition to have gksudo in front of the command?  This would open the gui or execute the command as root.

---

### Post by xjgnsdof on 2009-02-18
I thought about doing that, but because I am doing this from the "Places" sidebar in Nautilus (which I am not running as root), I do not see an easy way to change the result of clicking the eject button.

---

### Post by iaculallad on 2009-02-18
> **elgilicious said:**
> How do I set it so I can mount and unmount my NTFS partitions just by clicking a button?

Try to use the chown and chmod terminal utility to change the privilege on your mount point for the /dev/sda1 partition. To do this, try checking your /etc/fstab file.

```
sudo chown -R username:username /mount/point/here
```

then

```
sudo chmod -R 755 /mount/point/here
```

---

### Post by xjgnsdof on 2009-02-18
How do I input the mount point? As "/dev/sda1" or as "/media/Windows"?

**Edit:** My mount point is /media/Windows XP Home SP3, which I input into the command line as "/media/Windows\ XP\ Home\ SP3" without the quotes. I still get the same error message when I try to unmount the partition in Nautilus.

---

### Post by smo0th on 2009-02-19
as /media/wind0ze

---

### Post by mtopro on 2009-02-19
```
sudo fdisk -l
```
Do this to identify device..  Is it /dev/sda1 ?

then

```
sudo mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

---

### Post by xjgnsdof on 2009-02-19
I know how to mount and unmount partitions in the command line. I want to know how to do so through the little eject icon next to each partition's name in Nautilus' "Places" sidebar.

---

### Post by mtopro on 2009-02-19
I also have 8.10 64bit and don't have any issues.  Of course I don't use NTFS..  I am able to simply click on the drive and it mounts automatically. click the eject and it unmounts..

NTFS and permissions can be glitchy at times though especially through USB.

---

### Post by xjgnsdof on 2009-02-19
On my other PC running 8.10, when I try to mount an NTFS partition, a window pops up to ask for my root password. Then, the partition mounts. Why don't I get that pop-up on both computers, only one?

---

