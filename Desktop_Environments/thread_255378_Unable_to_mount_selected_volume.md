---
title: "Unable to mount selected volume"
date: 2006-09-11
forum: Desktop Environments
---

### Post by checkeredshawn on 2006-09-11
I tried to access my hard drive (partition?) which has Windows XP installed on it, but I get the error message 

error: device /dev/sda2 is not removable

error: could not execute pmount

I've tried editing /etc/pmount.allow but don't really know how to go about doing it.  Any help is appreciated :)

---

### Post by meng on 2006-09-11
This is covered in a wiki.
[http://help.ubuntu.com/community/MountingWindowsPartitions](http://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by ape on 2006-09-11
From an earlier thread on this same problem:

July 18th, 2006, 02:33 PM
I have found the answer !!

(I'm new to this though so bare with me if anything is wrong.)

The problem is when clicking on 'Places' then 'Computer' in ubuntu 6.06. The windows partitions which are automatically detected are not accessible, and you receive the following error:-

Unable to mount the selected volume
error: device /dev/hda2 is not removable
error: could not execute pmount

This is because pmount is being used by the system instead of mount. pmount is used because it can be executed by normal users. However pmount is designed for removable media and only if the user has the permission to mount removable devices.

I looked in the help for pmount, by typing 'man pmount' and found that non-removable devices can also be mounted if they are listed in the pmount.allow file.

So edit the file and add the device to the end of the file. In my case I typed 'sudo vi /etc/pmount.allow'

Then navigated to the end of the file. Pressed 'a' for append. Then typed the device. For me that was:-

/dev/sdb1

I then saved the file by typing

Esc : wq Enter

I was then able to mount the partition using the browser.

Hope that helps, its been very interesting learning this so far!

---

### Post by jperez on 2006-09-11
This works for me on both Windows XP Home and Pro hard drives:

```
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

If that doesn't work, then just change **hda1** to **sda1**.

Hope this helps!

Jesse~

---

### Post by checkeredshawn on 2006-09-11
Whoa, thanks everyone :)  Such fast responses, I really appreciate it.  For the record, I used the wiki and it worked.  I guess when I first edited /etc/pmount.allow I forgot to right click and mount the drives.  Thanks again!

---

### Post by BerkeleyDude on 2006-09-11
To mount non-removable partitions, you should probably be using the regular "mount" program. You might want set up /etc/fstab for that.

First of all, try to mount it as jperez suggested - only use sda2 instead of hda1. You can also change umask to give different permissions. If that works, then you can change /etc/fstab to have it mounted automatically.

Add an entry that looks like this:
/dev/sda2    /media/windows     ntfs    nls=utf8,umask=0222   0       0

If you don't want it to mount automatically, but you do want to mount it without using sudo, you can use this instead:
/dev/sda2    /media/windows     ntfs    nls=utf8,umask=0222,noauto,user   0       0

Good luck

---

### Post by pixelchutes on 2006-12-17
> **jperez said:**
> This works for me on both Windows XP Home and Pro hard drives:

```
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

If that doesn't work, then just change **hda1** to **sda1**.

Hope this helps!

Jesse~

@Jesse--

Thank you, this was the first step in mounting my Windows volume. (Wish I would have ordered Server Edition Ubuntu CD) ...no worries.

I was able to mount this volume, and see all needed files my sister's Virus-heavy XP machine was preventing us from accessing. Once backed up, I'll wipe the drive and install Ubuntu for good.

Any recommendations on backing up needed files over the network (1 Ubuntu machine via Ubuntu CD, and 1 Windows XP Pro machine, same network via Linksys router...)

I've never networked two alternate machines like this in a home network. Can my windows machine see the Ubuntu machine??

**Update:**  *Nice!*...ah the joys of simple computing ;)

I opted to install proFTP on my ubuntu box, and BulletProof FTP Server on my XP machine. First-time proFTP user here, and worked flawlessly!

```

sudo apt-get install proftpd

```

Backed up 2GBs @ an avg. of ~5 Mb/sec, so the wait wasn't unbearable.

---

