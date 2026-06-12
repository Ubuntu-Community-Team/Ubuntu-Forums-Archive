---
title: "some permission issues viewing ntfs drive using fuse"
date: 2006-06-22
forum: Desktop Environments
---

### Post by BlakeEM on 2006-06-22
my fstab is like this

/dev/sda5     /media/sda5    ntfs-fuse       auto,gid=1001,umask=0007       0       0

For some reason it doesn't auto mount for me at startup.

First it tells me that I don't have permission to mount it so I manually sudo mount it and then when I try to access it I'm told 

"You do not have the permissions necessary to view the contents of "sda5"."

I did create the ntfs group and I added my user to it.

I was able to view a file listing using sudo so I know my paths are all correct. (forgot what command I used to do that, I can't find it anymore)

when I try
"sudo dmesg > /media/sda5/my_dmesg_log.txt"
I get "bash: /media/sda5/my_dmesg_log.txt: Permission denied"

Thanks for any help

~Blake

---

### Post by gerbman on 2006-06-22
[QUOTE=BlakeEM]my fstab is like this

/dev/sda5     /media/sda5    ntfs-fuse       auto,gid=1001,umask=0007       0       0[/QUOTE]Why not just use "ntfs" for the filesystem type instead of ntfs-fuse?> First it tells me that I don't have permission to mount it so I manually sudo mount it and then when I try to access it I'm told

"You do not have the permissions necessary to view the contents of "sda5"."Try adding the option "uid=username" to your fstab line, where "username" is your account - this will make you owner of the mounted filesystem.> when I try
"sudo dmesg > /media/sda5/my_dmesg_log.txt"
I get "bash: /media/sda5/my_dmesg_log.txt: Permission denied"In this case, sudo only applies to running dmesg (not piping the output into the file), and since you don't have write permissions on sda5 you can't access my_dmesg_log.txt. Adding the option mentioned above should fix this problem.

---

### Post by BlakeEM on 2006-06-22
that did it, thanks!

---

### Post by gerbman on 2006-06-22
[QUOTE=BlakeEM]that did it, thanks![/QUOTE]You're welcome :)

---

### Post by BlakeEM on 2006-06-22
wait one more small issue, when I try to run it from the "Computer" under places it tells me

"mount: according to mtab, /dev/sda5 is already mounted on /media/sda5

mount failed"

I can view it just fine by the sda5 folder however.

---

### Post by gerbman on 2006-06-22
[QUOTE=BlakeEM]wait one more small issue, when I try to run it from the "Computer" under places it tells me

"mount: according to mtab, /dev/sda5 is already mounted on /media/sda5

mount failed"

I can view it just fine by the sda5 folder however.[/QUOTE]Hmmm...I'm not sure. You could try unmounting and remounting the partition:```
sudo umount /path/to/sda5
sudo mount /path/to/sda5

```:-k

---

### Post by BlakeEM on 2006-06-22
still does the same thing.
it seems it's not seeing that it's mounted some reason.

---

### Post by gerbman on 2006-06-22
[QUOTE=BlakeEM]still does the same thing.
it seems it's not seeing that it's mounted some reason.[/QUOTE]Can you post your /etc/fstab and /etc/mtab files at the time when you get the error message?

---

### Post by Hairy_Palms on 2006-06-22
you could see if unmounting it then double clicking it in computer mounts it for you.

---

### Post by BlakeEM on 2006-06-23
[QUOTE=Hairy_Palms]you could see if unmounting it then double clicking it in computer mounts it for you.[/QUOTE]


when I do that I get this

"mount: only root can mount /dev/sda5 on /media/sda5"

---

### Post by BlakeEM on 2006-06-23
[QUOTE=gerbman]Can you post your /etc/fstab and /etc/mtab files at the time when you get the error message?[/QUOTE]


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda5     /media/sda5    ntfs-fuse       auto,uid=blake,gid=1001,umask=0007       0       0




/dev/hdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
/dev/sda5 /media/sda5 fuse rw,nosuid,nodev,default_permissions,allow_other 0 0

---

### Post by gerbman on 2006-06-23
Do you get the same result when using ntfs as the filesystem instead of ntfs-fuse?

---

### Post by BlakeEM on 2006-06-24
When I do just ntfs I see no icon at all under Computer and when I go to the mount point I get "You do not have the permissions necessary to view the contents of "download"."

I added me as a uid as well.

just ntfs read would be fine at this point if I could get one to work right.

---

### Post by gerbman on 2006-06-24
[QUOTE=BlakeEM]When I do just ntfs I see no icon at all under Computer and when I go to the mount point I get "You do not have the permissions necessary to view the contents of "download"."

I added me as a uid as well.

just ntfs read would be fine at this point if I could get one to work right.[/QUOTE]Try using the following line for your ntfs drive...I have used it in the past with success:```
/dev/sda5     /media/sda5     ntfs     defaults,uid=blake,ro     0     0
```

---

### Post by BlakeEM on 2006-06-28
Worked great, thanks!

---

