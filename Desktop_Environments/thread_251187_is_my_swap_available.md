---
title: "is my swap available?"
date: 2006-09-05
forum: Desktop Environments
---

### Post by hellfried on 2006-09-05
i have a swap partition on sda4 which is 1G in size. however when i run gkrellm i get a reading of 0M-0M free. if you look at the screen capture the partition is definitely 'accessible' when i look in disks manager. i share this swap partition with pclinuxos which sits on another partition. could this be a problem?

---

### Post by amo-ej1 on 2006-09-05
In a console, when you run  'free -m' does it contain a line showing your swap space statistics ?
Does the file /etc/fstab contain an entry like
```

/dev/sda4       none            swap    sw              0       0

```
This entry is used to identify the swap space and to mount it at boottime. Does 'dmesg | grep swap' show something like
```

k@lap:~$ dmesg | grep swap
[17179594.068000] Adding 979952k swap on /dev/sda4.  Priority:-1 extents:1 across:979952k

```

?

---

### Post by hellfried on 2006-09-05
> **amo-ej1 said:**
> In a console, when you run  'free -m' does it contain a line showing your swap space statistics ?
Does the file /etc/fstab contain an entry like
```

/dev/sda4       none            swap    sw              0       0

```
This entry is used to identify the swap space and to mount it at boottime. Does 'dmesg | grep swap' show something like
```

k@lap:~$ dmesg | grep swap
[17179594.068000] Adding 979952k swap on /dev/sda4.  Priority:-1 extents:1 across:979952k

```

?


this is how my fstab looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       /media/sda5     ext3    defaults        0       2
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda4  swap  sw   none   0   0

however when i do 'dmesg | grep swap' i get nothing.

---

### Post by tturrisi on 2006-09-05
What does System Monitor say?
Applications > System Tools > System Monitor > Resources Tab

Which Gkrellm builtin module are use talking about...Memory?

Here's a screenshot of my Gkrellm w/ Memory builtin:

[IMG]http://members.cox.net/aturrisi/gkrellm.png[/IMG]

---

### Post by hellfried on 2006-09-05
> **tturrisi said:**
> What does System Monitor say?
Applications > System Tools > System Monitor > Resources Tab

Which Gkrellm builtin module are use talking about...Memory?

Here's a screenshot of my Gkrellm w/ Memory builtin:

[IMG]http://members.cox.net/aturrisi/gkrellm.png[/IMG]

it says 0M-0M free

---

### Post by nikhilk on 2006-09-05
Open a terminal and do the following
```
sudo mkswap /dev/sda4
sudo swapon /dev/sda4
```

Does this help?

---

### Post by taurus on 2006-09-05
If you look at your /etc/fstab again, you see that the entry for your swap partition is wrong...

```

/dev/sda4   none   swap   sw   0   0

```

---

### Post by hellfried on 2006-09-05
> **taurus said:**
> If you look at your /etc/fstab again, you see that the entry for your swap partition is wrong...

```

/dev/sda4   none   swap   sw   0   0

```

ok that did the trick! thanks man. i actually got the original code from another thread. i guess that person is wrong. now gkrellm shows 1004M - 1004M free for swap.

---

### Post by taurus on 2006-09-05
Glad to hear that your system is "seeing" your swap now.

---

### Post by LeslieL on 2006-09-06
Thanks for asking this question and answering it. I clobbered my swap partition by playing around with gparted and you fixed it for me!

---

### Post by archis on 2006-10-22
Just wanted to add this little rant:

If your swap file is located on a secondary, removable drive (a USB drive for example) and the drive fails to initialize fast enough during startup, the swap might not get added at the time. This is because the boot process doesn't wait (forever) for external drives to initialize and might just move on (with Dapper at least). In any case, once you log in, the USB drive will mount and appear on your desktop, but if your swap file is located on that drive, fstab will not have brought it online. This means you might have to turn it on manually.

Check with 'free -m' whether your swap file is online, and if it's not, just invoke 'sudo swapon -a'.

Just saying.

---

