---
title: "Error message after update"
date: 2005-12-09
forum: General Help
---

### Post by claus on 2005-12-09
Hi,

after installing "Breezy" successfully on my PC (AMD K6 2) I am getting the following error message after confirming the upgrades suggested:
```

E: /var/cache/apt/archives/linux-image-2.6.12-10-386_2.6.12-10.24_i386.deb: failed in buffer_write(fd) (10, ret=-1)

```
What does this mean actually, and how can I fix this?

---

### Post by blueplazma on 2005-12-09
How much free space do you have left on your hard disk?  It sounds like there's an error trying to write to your drive.

---

### Post by claus on 2005-12-09
[QUOTE=blueplazma]How much free space do you have left on your hard disk?  It sounds like there's an error trying to write to your drive.[/QUOTE]

I manually partitioned my harddrive completely anew. Here's the result of **df -h**:

```

ccyrny@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda5             4.7G  391M  4.3G   9% /
tmpfs                 126M     0  126M   0% /dev/shm
tmpfs                 126M   13M  114M  10% /lib/modules/2.6.12-9-386/volatile
/dev/hda1             7.4M  7.4M     0 100% /boot
/dev/hda8              17G   40M   17G   1% /home
/dev/hda7             9.4G  1.2G  8.3G  12% /usr 

```
In a German Debian forum I read the suggestion to set a symbolic link from **/var/foo** to **/usr/src**, but I do have enough space left.

---

### Post by Meurglys on 2006-05-05
The same thing just happened to me with today's kernel update to 2.6.12-10.32 . Did you ever fix it? And if so, how?

Same error:
E: /var/cache/apt/archives/linux-image-2.6.12-10-386_2.6.12-10.32_i386.deb: failed in buffer_write(fd) (10, ret=-1)

I have 2.5 GB free space on that partition ... :confused:

---

### Post by Meurglys on 2006-05-05
Fixed it. Didn't have anything to do with the var partition.

There wasn't enough space in the root partition! Removed one of the older linux-images and voilà - new image installs without problems.

Feeling kinda stupid now. :oops:

---

