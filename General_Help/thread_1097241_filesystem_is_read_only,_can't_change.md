---
title: "filesystem is read only, can't change"
date: 2009-03-15
forum: General Help
---

### Post by drunkmatador on 2009-03-15
I'm having a really tough problem with my installation. I used to have half of my hard drive in a fat32 partition which had windows installed on it. Earlier I decided to back up what i needed from it and delete the partition, leaving in place a free ext2 partition i can use with ubuntu.

The partition deleted fine but it was the only one marked bootable, so I made my primary linux partition bootable because i didn't want to get stuck not being able to boot my computer.

Now the partition is all read-only and it boots up but i can't delete any files. What makes this especially annoying is that the partition is full so i've got to delete files. When I run sudo nautilus it says "** ERROR **: Cannot find a safe socket path in '/tmp'" and doesn't start up.

Please help!

---

### Post by taurus on 2009-03-15
Where do you mount that new ext2 partition?  You just need to change the ownership of the mount point of that partition from root to your login name.  Then, you can write to it anytime you want.  

Open a terminal and post the outputs of these commands.

```
sudo fdisk -l
cat /etc/fstab
df -h
id
```

p.s.  And you should consider using _gksu/gksudo_ when you run nautilus instead of just sudo.

```
gksudo nautilus
```

---

### Post by drunkmatador on 2009-03-15
mozzles@mozzles-laptop:~$ sudo fdisk -l
[sudo] password for mozzles: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x282d282d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7295    58597056   83  Linux
/dev/sda2            7296        7538     1951897+  82  Linux swap / Solaris
/dev/sda3            7539       14592    56661255   83  Linux

mozzles@mozzles-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=958d6092-3725-48e8-a0ca-0d132d405e55 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=2a0f3acd-ce77-4d25-abd0-9ddfc8cecb68 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


mozzles@mozzles-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              56G   53G  168M 100% /
varrun                466M  136K  466M   1% /var/run
varlock               466M     0  466M   0% /var/lock
udev                  466M   52K  466M   1% /dev
devshm                466M  412K  466M   1% /dev/shm
lrm                   466M   45M  422M  10% /lib/modules/2.6.24-24-rt/volatile
gvfs-fuse-daemon       56G   53G  168M 100% /home/mozzles/.gvfs
/dev/sda3              54G  6.9G   45G  14% /media/disk


mozzles@mozzles-laptop:~$ id
uid=1000(mozzles) gid=1000(mozzles) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),124(mythtv),1000(mozzles)

---

### Post by taurus on 2009-03-15
First, unmount /dev/sda3 from /media/disk.

```
sudo umount /dev/sda3
df -h
```

Now, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda3   /media/sda3   ext2   defaults   0   2
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/sda3
sudo mount -a
df -h
```
Next step is to change the ownership of /media/sda3 from root to your login name, mozzles.

```
sudo chown -R mozzles:mozzles /media/sda3
ls -la /media
```

---

### Post by drunkmatador on 2009-03-15
When I try and open /etc/fstab it says "Read-only file system" and opens a small blank window. Not a blank document but a window that is all white.

---

### Post by taurus on 2009-03-15
What was the exact command that you ran to "open" /etc/fstab?

---

### Post by drunkmatador on 2009-03-15
The one you told me to use, of course.

gksudo gedit /etc/fstab

---

### Post by taurus on 2009-03-15
How about

```
sudo nano -Bw /etc/fstab
```
Does it look something like this?

```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=958d6092-3725-48e8-a0ca-0d132d405e55 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda2
UUID=2a0f3acd-ce77-4d25-abd0-9ddfc8cecb68 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

```

---

### Post by drunkmatador on 2009-03-15
Yeah that worked, I hadn't thought of opening it in nano. It looks exactly like that. Now I just add that line and it should let me save right?

---

### Post by taurus on 2009-03-15
Save and exit with <Ctrl>x.

---

### Post by drunkmatador on 2009-03-15
[ Error writing /etc/fstab: Read-only file system ]

---

### Post by drunkmatador on 2009-03-15
Another thing, you understand that I'm not talking about the partition that used to be fat32, but the one which has always had ubuntu on it, right? I think that the other one works fine.

---

### Post by taurus on 2009-03-15
> **drunkmatador said:**
> 
mozzles@mozzles-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
**[COLOR="Red"]/dev/sda1              56G   53G  168M 100% /[/COLOR]**
varrun                466M  136K  466M   1% /var/run
varlock               466M     0  466M   0% /var/lock
udev                  466M   52K  466M   1% /dev
devshm                466M  412K  466M   1% /dev/shm
lrm                   466M   45M  422M  10% /lib/modules/2.6.24-24-rt/volatile
gvfs-fuse-daemon       56G   53G  168M 100% /home/mozzles/.gvfs
/dev/sda3              54G  6.9G   45G  14% /media/disk


Okay, the reason you cannot edit or save anything because you already maxed out your root partition--/.  You need to do some serious house cleaning, removing stuff that you don't need like emptying your trash bin and such.

```
sudo apt-get clean
sudo apt-get autoremove
df -h
```

---

### Post by drunkmatador on 2009-03-15
It's not letting me do any of those. Is there any way I can change permissions on a few large files and then delete them?

mozzles@mozzles-laptop:~$ sudo apt-get clean
[sudo] password for mozzles: 
W: Not using locking for read only lock file /var/cache/apt/archives/lock
mozzles@mozzles-laptop:~$ sudo apt-get autoremove
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

---

### Post by taurus on 2009-03-15
Reboot and at the GRUB menu, pick recovery mode.  Then get into root shell and run

```
apt-get clean
apt-get autoremove
```
Now, remove those large files that you don't need anymore with the rm command (rm filename).  You can check to see how much space you have saved by running this command anytime.

```
df -h
```
You can boot into normal with **exit**.

---

### Post by drunkmatador on 2009-03-15
Ok i did that and freed up some space, now should i try and edit the etc/fstab file again?

---

### Post by taurus on 2009-03-15
Yes.

---

