---
title: "How do I change permissions from only root to anyone can mount/unmount partitions"
date: 2009-03-17
forum: General Help
---

### Post by ozguitarplayer on 2009-03-17
Hi,
Now when I boot into Hardy Heron I have one partition on /dev/sdb1 (mounted as /media/Doze) on my desktop, if I try to unmount it I am told...

You are not privilegded to unmount the volume 'Doze'

The only way I can unmount it is using terminal...sudo umount /media/doze

..any ideas on how to not have the partition on the desktop when I open ubuntu

..and how can I change the permissions so that I don't have to be root to mount/unmount the partition?

---

### Post by iaculallad on 2009-03-17
> **ozguitarplayer said:**
> 
..any ideas on how to not have the partition on the desktop when I open ubuntu

Remove the partition entry on your /etc/fstab file.

> **ozguitarplayer said:**
> 
..and how can I change the permissions so that I don't have to be root to mount/unmount the partition?

```
sudo chown -R your_name:your_name /media/doze
sudo chmod -R 755 /media/doze
```

---

### Post by ozguitarplayer on 2009-03-17
Thanks isculallad, 
I removed the entry from /etc/fstab however haven't rebooted yet

when I run the second command I get..

nigel@ubu8:~$ sudo chown -R nigel:nigel /media/Doze
[sudo] password for nigel: 
nigel@ubu8:~$ sudo chmod -R /media/Doze
chmod: missing operand after `/media/Doze'
Try `chmod --help' for more information.
nigel@ubu8:~$ 

 what does.....missing operand after `/media/Doze'....mean?

---

### Post by iaculallad on 2009-03-17
> **ozguitarplayer said:**
> 
 what does.....missing operand after `/media/Doze'....mean?

You forgot to include the numeric permission:

```
sudo chmod -R **755** /media/Doze
```

---

### Post by ozguitarplayer on 2009-03-17
yeh right :-) woops 
again, many thanks iaculallad, all back to normal

---

### Post by dbuurman on 2009-03-17
How about using the 'option' field in your fstab file?

From: [http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab)

**user / users / nouser**
[I]user permits any user to mount the filesystem. This automatically implies noexec, nosuid, nodev unless overridden. If nouser is specified, only root can mount the filesystem. If users is specified, every user in group users will be able to unmount the volume.
[/I]
**auto / noauto**
[I]With the auto option, the device will be mounted automatically at bootup or when the mount -a command is issued. auto is the default option. If you don't want the device to be mounted automatically, use the noauto option in /etc/fstab. With noauto, the device can be only mounted explicitly.
[/I]

/edit:

So, in my opinion, you could leave the entry for your /dev/sdb1 in your fstab file using the options 'noauto,user' to make sure it won't get mounted at boot-time but can be mounted without having to use root privileges.

---

### Post by ozguitarplayer on 2009-03-17
thanks I'll try that also..

---

### Post by dbuurman on 2009-03-17
Well, by using the fstab you can easily mount your filesystems without having to specify both filesystem and mountpoint, one of these will be sufficient.

---

