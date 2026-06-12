---
title: "Mounted NAS Permissions"
date: 2009-05-11
forum: Desktop Environments
---

### Post by Mongo5000 on 2009-05-11
I have my NAS mounted in fstab as follows
```
//192.168.0.200/PUBLIC /home/stephen/Storage cifs rw,defaults,errors=remount-rw 0       0
```

NAS is a MyBookWorld World Edition 2.  The 1TB model here 

Mounts fine, problem is that I don't have write permissions.  If I use the Connect to Server option from the Places menu, I get write permissions but don't want to use it this way.

How can I change my fstab to allow me write permissions?

---

### Post by Peter09 on 2009-05-11
Check the options on the actual mount point.

/home/stephen/Storage

---

### Post by Mongo5000 on 2009-05-11
Permissions tab says owner is root.  Group is www-data

Should I just make myself a member of www-data group?

---

### Post by Peter09 on 2009-05-11
No you should be the owner , as I presume its mounted in your home directory.

---

### Post by Mongo5000 on 2009-05-11
ya, its mounted in my home directory.

NAS doesn't require authentication so not sure how to make myself owner

---

### Post by Peter09 on 2009-05-11
We are not talking about the NAS - this is about the directory upon which you are mounting the NAS file system. The  NAS is totally out of the loop here.

---

### Post by Mongo5000 on 2009-05-11
Gotcha.

Since I created the Storage folder why wouldn't it automatically make me the owner?  I'm assuming what I need to do is change the permissions so im the owner of the Storage directory.

Do I understand that right?

EDIT: I also have a similar mount in my Music folder in my home directory.  Same thing regarding the permissions.

---

### Post by Peter09 on 2009-05-11
Thats right you need write access to those directories.

---

### Post by Mongo5000 on 2009-05-11
> **Peter09 said:**
> Thats right you need write access to those directories.

ok, so im not that comfortable with changing permissions with the prompt yet so I am doing it through nautilus.

Opened nautilus as root, went to permissions of Storage and when I try to change the settings, I get the following error.

```
Could not change the owner of "Storage": Error setting owner: Invalid argument
```

From what I know, this is how I would do it via terminal
```
chmod a+w Storage
```

---

### Post by Mongo5000 on 2009-05-11
So did some reading, just want to clarify this before I actually do it.

If I want to change the owner of my Storage directory to myself, I would do the following

```
sudo chown -R stephen /home/stephen/Storage
```

Am I right?

EDIT:  So I tried "sudo chown stephen /home/stephen/Storage" and I get that Invalid argument error again.

---

### Post by Peter09 on 2009-05-11
don't think you want the -R as that will change all the way through the lower directories, i.e your NAS

---

### Post by Mongo5000 on 2009-05-11
Even without the -R it doesn't work.  Still getting that invalid argument error regardless of what I do.

Do the directories need to be unmounted before I chown it?

---

### Post by Peter09 on 2009-05-11
Can you post the command that you used

---

### Post by Mongo5000 on 2009-05-11
> **Peter09 said:**
> Can you post the command that you used
```

sudo chown stephen /home/stephen/Storage
```

---

### Post by zacktu on 2009-05-11
I use my NAS only for backup, so I use a command instead of an entry in fstab.  The command is less complex than your fstab entry.  I'm away from home, so I can't do a mount to see the fstab entry that results from the command.  Here's the command from my bin directory:

sudo mount -t cifs -o nounix //storage/mozart /mnt/mozartonstorage

/mnt has permissions 755, and all the directories in /mnt have permissions 755.  All are owned by root.

The ip address for storage is in /etc/hosts.

---

### Post by Peter09 on 2009-05-11
Just thought - you will need to unmount the directory first.

---

### Post by Mongo5000 on 2009-05-11
So I unmounted the directories, changed owner, mounted again and now I got write permission.

That problem solved :D

What I do notice now is that once im into my nas, all subfolders have no write permission so Im assuming that -R should be used to change permissions.

What I don't understand is I changed the permission on a directory located on my PC.  If I use the chown -R, it will change the permissions of the directories in the NAS itself right?  

What will happen if I do use the -R?

---

### Post by Peter09 on 2009-05-11
I would be careful doing that, do you know why you do not have write permissions on the NAS?

---

### Post by Mongo5000 on 2009-05-11
> **Peter09 said:**
> I would be careful doing that, do you know why you do not have write permissions on the NAS?

To be honest, I have no clue.  Would you mind explaining?

Another thing I don't understand is why when I use the Connect To Server from the places menu to access my NAS, it works like a dream.  Read & Write on everything.

---

### Post by Peter09 on 2009-05-11
What does the command

```
mount -l
```

show

---

### Post by Mongo5000 on 2009-05-11
> **Peter09 said:**
> What does the command

```
mount -l
```

show

stephen@ubuntu:~$ mount -l
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro) []
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/stephen/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=stephen)
//192.168.0.200/PUBLIC on /home/stephen/Storage type cifs (rw,mand)

---

### Post by Peter09 on 2009-05-11
Do you know how you are being authenticated? Does your NAS have authentication set?

---

### Post by Mongo5000 on 2009-05-11
NAS doesn't have any authentication.

There is a master login for the interface, but nothing to access it.

Like in Windows, I just map network drive and its good to go.  Same with the connect to server in linux.

---

### Post by Mongo5000 on 2009-05-11
Spoke too soon, tried to create a directory within Storage, permission denied.

---

