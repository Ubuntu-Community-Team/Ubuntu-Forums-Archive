---
title: "Running programs from hard drive under live session"
date: 2009-04-26
forum: General Help
---

### Post by mrl777 on 2009-04-26
Hello,

I have a nutty question.

How would one go about running programs under live session that are installed on a hard drive.  Lets say I need to boot using the live session disk, yet I needed to gain access to the hard drive programs.  Could this be easily done?

---

### Post by perrti-y02 on 2009-04-26
I would have thought that if you navigate your way to /usr/bin in your normal operating system's hard drive you could run any of the programs there. I would have thought the command would look something like

/media/disk0/usr/bin/amarok

A bit of a guess but I think it is sound.

---

### Post by unutbu on 2009-04-26
Boot the LiveCD. Open a terminal (Applications>Accessories>Terminal)

You need to know the device name of your root (Linux) partition. If you do not know it, 
type 
```

sudo fdisk -l
```

(lower case "L", not a one).

Once you know the correct device name (e.g. /dev/sda5), type
```

sudo mount **/dev/sda5** /mnt  # Change /dev/sda5 to the correct device name.

```

Your Linux partition is now located at /mnt.
In agreement with perrti-y02's method, you can now run programs from the command-line, 
by typing in their full path's starting from /mnt: For example,
```

/mnt/usr/bin/amarok

```
However, some apps may require access to system resources in /proc, /sys, or /dev.
You may also wish to run programs as your normal user, not as "ubuntu". In that case,
type

```

cd /mnt
sudo mount --bind {/,}proc
sudo mount  --bind {/,}sys
sudo mount  --bind {/,}dev
sudo chroot /mnt
grep -v rootfs /proc/mounts > /etc/mtab
mount -a

```

This will give you a root shell, as though you had booted your hard drive's Linux operating system.

If you want to execute programs as a normal user, now type
```

sudo su USERNAME -
```

Now you can type commands to launch whatever program you like as user USERNAME.

---

