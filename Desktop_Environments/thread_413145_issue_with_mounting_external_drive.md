---
title: "issue with mounting external drive"
date: 2007-04-18
forum: Desktop Environments
---

### Post by jord1242 on 2007-04-18
Initially, Edgy was recognizing and auto mounting my external NTFS external USB drive. I unhooked it from the machine and when I re-hooked it up, it didn't auto mount - I was a bit frustrated.

Then I decided to manually mount it. I ran

```
sudo mount -o defaults -t ntfs /dev/sdc1 /media/tonyromo
```This mounts the drive fine for me, but when I try and access it

```
bash: cd: tonyromo: Permission denied
```It appears that because I am not root (the owner) I cannot access the drive. I cannot figure out how to manually mount this so I can access this as a normal user.

I also want this to automatically mount (like it was before) but not sure exactly what to add to /etc/fstab - I tried a couple things but neither worked, and just wanted to know if someone could point me in the right direction.

Finally, I want the ability to write to this drive, I installed ntfs-3g and tried to mount it that way.

```
sudo mount -o defaults -t ntfs-3g /dev/sdc1 /media/tonyromo
```I get the following error. I think the ntfs-3g is setup correctly.

```
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdc1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run 'ntfsfix' on Linux unless you have Vista, then mount NTFS with
   the 'force' option read-write, or with the 'ro' option read-only.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.
```Not sure what is going on. Any help would be appreciated. I am a noob still :)

JJ

---

### Post by taurus on 2007-04-18
Try

```
sudo umount /dev/sdc1
sudo mount -t ntfs /dev/sdc1 /media/tonyromo -o nls=utf8,umask=0222
ls -la /media/tonyromo
```

---

### Post by jord1242 on 2007-04-19
Magic! Thank you so much, not sure about the umask permissions thing, but that worked great.

Now, how do I get write permissions to that drive? I tried copying into it, and it was a no go. Can I use ntfs-3g?

Also, I am under the impression I can now add that line to /etc/fstab and it will auto remount the drive for me?

Thanks again for the help, that was exactly what I wanted.

JJ

---

### Post by taurus on 2007-04-19
Here's a link about writing to ntfs with ntfs-3g driver.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by jord1242 on 2007-04-19
> **taurus said:**
> Here's a link about writing to ntfs with ntfs-3g driver.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Taurus,

I will give that a look over, thanks again for all the help. One further question, by mounting this, it will add the entry automatically to my /etc/fstab so that it will auto mount next time? Or do I have to manually add the entry?

I would try it now, but I am at work, and won't be home for a while. THanks again!!

JJ

---

### Post by Wake Rider on 2007-04-24
I'm having the same difficulty as jord1242. Except the lines of code that were pasted there didn't work for me. I have tried force mounting the drive but even that didn't work. 
What is the command to "clean" the drive so it will be accepted by Ubuntu again?

I tried ntfsfix and that said the operation completed successfully but the disk was still unusable.

jason@jason-desktop:~$ ntfsfix /dev/sda1
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS partition /dev/sda1 was processed successfully.

 I tried entering a force mount:

jason@jason-desktop:~$ sudo mount -t ntfs-3g /dev/sda1 /media/usb_disk -o force

WARNING: Dirty volume mount was forced by the 'force' mount option.
fusermount: failed to access mountpoint /media/usb_disk: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sda1 (usb_disk)

What do I do now?

---

### Post by Wake Rider on 2007-04-24
I fixed my problem. I attached the USB drive to Windows and did a scan disk and used the 'Safely Remove Hardware' Option. Linux accepted the drive perfectly after that, both read and write.

---

### Post by jord1242 on 2007-04-24
Good to know, although ntfsfix should work. It did for me. I then moved everything off of it, reformatted as FAT32 (so that it can be plugged into a windows box), and I can now read/write to it. I could never get the ntfs-3g drivers working.

JJ

---

