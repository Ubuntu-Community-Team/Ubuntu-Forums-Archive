---
title: "Um, help..."
date: 2009-02-23
forum: General Help
---

### Post by Dbzdude707 on 2009-02-23
I think I nearly bricked my laptop...

Well, my Ubuntu installation was acting up by giving me kernel panic half the time I tried to boot it up, so I decided I'd uninstall it and reinstall it later. I did some quick research and found that the best way to do this is to mount the Ubuntu partition in Windows and format it.

Um... Apparently I was horribly wrong... I got a blue screen halfway through the formatting process and now the GRUB loader thingie won't load any OS, period.

I have Windows Vista Basic also installed on this laptop, it was setup to dual boot.

I got out the old Ubuntu installation disk (it was the most recent for Ubuntu Desktop, 8.10 intrepid), and now I'm running Ubuntu off the live cd. So perhaps that indicates that it's not completely bricked? I hope I can do something with this...

What should I do? Or perhaps you could point me to a better place to ask for help.

---

### Post by mtopro on 2009-02-23
Have you tried to test your system memory to insure that the kernel panic is not brought on by faulty memory thus writing bad information to your hard disk and corrupting the installs?

I think you can do a memtest from the Ubuntu Live CD.  You can for sure do it from the grub menu.

---

### Post by taurus on 2009-02-23
From the Ubuntu LiveCD, open a terminal and have a quick look at your partition table.

Applications -> Accessories -> Terminal
```
sudo fdisk -**l**
```
That should be a lower case letter L, not number 1.

p.s.  Are you planning to reinstall Ubuntu on your laptop again, dualbooting with windows?

---

### Post by Dbzdude707 on 2009-02-23
> **mtopro said:**
> Have you tried to test your system memory to insure that the kernel panic is not brought on by faulty memory thus writing bad information to your hard disk and corrupting the installs?

I think you can do a memtest from the Ubuntu Live CD.  You can for sure do it from the grub menu.

Sorry but the problem is no longer that I have kernel panic... The problem is that now GRUB won't load anything, it just says "Error 17" I think.

Anyways, as I said, I mounted and formatted the Ubuntu partition using Vista... Then, halfway through that process it blue screen'd me and now GRUB just gives errors instead of booting anything.

I'm currently sending this message using the Live CD.

Also, I did the memory test and it passed it, it didn't give errors.

One more thing, I used this to mount the partition in windows:

[http://ext2fsd.sourceforge.net/projects/projects.htm](http://ext2fsd.sourceforge.net/projects/projects.htm)

---

### Post by Dbzdude707 on 2009-02-23
> **taurus said:**
> From the Ubuntu LiveCD, open a terminal and have a quick look at your partition table.

Applications -> Accessories -> Terminal
```
sudo fdisk -**l**
```
That should be a lower case letter L, not number 1.

p.s.  Are you planning to reinstall Ubuntu on your laptop again, dualbooting with windows?
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x307b307b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7768    62396428+   7  HPFS/NTFS
/dev/sda2            7769        9729    15751732+   5  Extended
/dev/sda5            7769        9641    15044841    7  HPFS/NTFS

Disk /dev/sdb: 4005 MB, 4005560320 bytes
16 heads, 32 sectors/track, 15280 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              16       15280     3907648    7  HPFS/NTFS

```

That's what I get when doing what you told me to do. It won't mount any of my drives though, not even the USB stick I had inserted when I got the blue screen. O.o

Yes I plan to reinstall ubuntu to dual boot.

If it matters, and it probably does... I don't have the CD for Vista, so this installation of it is all I got... I hope I didn't lose it. >_<

---

### Post by taurus on 2009-02-23
Do you want to reinstall Ubuntu on /dev/sda5 since I assume you have your vista on the first partition, /dev/sda1?

---

### Post by Dbzdude707 on 2009-02-23
> **taurus said:**
> Do you want to reinstall Ubuntu on /dev/sda5 since I assume you have your vista on the first partition, /dev/sda1?
Sorry but I'm new to this... Can you explain to me what those are? I assume those are more technical terms for the different partitions.

If you mean that all I had to do all along was use the CD to install it over the previous Ubuntu installation, then I've officially found a facepalm moment... X_X;

---

### Post by taurus on 2009-02-23
Those are your partitions of your harddrive.

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x307b307b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7768    62396428+   7  HPFS/NTFS
/dev/sda2            7769        9729    15751732+   5  Extended
/dev/sda5            7769        9641    15044841    7  HPFS/NTFS

```

---

### Post by Dbzdude707 on 2009-02-23
> **taurus said:**
> Those are your partitions of your harddrive.

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x307b307b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7768    62396428+   7  HPFS/NTFS
/dev/sda2            7769        9729    15751732+   5  Extended
/dev/sda5            7769        9641    15044841    7  HPFS/NTFS

```
Alright then, yeah. I'm not sure which one is Vista, but I assume that the sda1 one is...

---

### Post by mtopro on 2009-02-23
Sounds like you are on the right track for getting Ubuntu reinstalled.  However don't discount the memory thing.  It takes a bit of time to check.  Make sure you go through at least 1 full PASS.  It wouldn't be much fun if you had to start over again because there is a memory issue.

---

### Post by Dbzdude707 on 2009-02-23
> **mtopro said:**
> Sounds like you are on the right track for getting Ubuntu reinstalled.  However don't discount the memory thing.  It takes a bit of time to check.  Make sure you go through at least 1 full PASS.  It wouldn't be much fun if you had to start over again because there is a memory issue.
No, I got a full pass and then stopped it.

So now what do I need to do? Install it on the sda5 using the CD?

---

### Post by tad1073 on 2009-02-23
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by taurus on 2009-02-23
Better double check before you proceed just in case there is something on /dev/sda5.  Mount it and see if it is really empty.

```
sudo mkdir /media/sda5
sudo mount -t ntfs-3g /dev/sda5 /media/sda5
ls -la /media/sda5
```
What is the output of the last command?

---

### Post by Dbzdude707 on 2009-02-23
> **taurus said:**
> Better double check before you proceed just in case there is something on /dev/sda5.  Mount it and see if it is really empty.

```
sudo mkdir /media/sda5
sudo mount -t ntfs-3g /dev/sda5 /media/sda5
ls -la /media/sda5
```
What is the output of the last command?

```
ubuntu@ubuntu:~$ sudo mkdir /media/sda5
mkdir: cannot create directory `/media/sda5': File exists
ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda5 /media/sda5
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 /media/sda5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 /media/sda5 ntfs-3g force 0 0
ubuntu@ubuntu:~$ ls -la /media/sda5
total 0
drwxr-xr-x 2 root root 40 2009-02-24 00:23 .
drwxr-xr-x 3 root root 80 2009-02-24 00:23 ..

```

...Yeah... This is probably a big problem.

---

### Post by Dbzdude707 on 2009-02-23
For that restore GRUB thing, I got this...

```
grub> find /boot/grub/stage1

Error 15: File not found

```

That was after I used "sudo grub" in the terminal.

---

### Post by tad1073 on 2009-02-23
Looks like to me you need to reinstall Ubuntu or if you have a vista dvd reinstall the mbr.

---

### Post by taurus on 2009-02-23
Use the force option to mount it.

```

sudo mount -t ntfs-3g /dev/sda5 /media/sda5 -o force
ls -la /media/sda5

```

---

