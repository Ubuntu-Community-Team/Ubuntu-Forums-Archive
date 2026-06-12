---
title: "Error: Cannot load entry"
date: 2006-04-18
forum: Desktop Environments
---

### Post by ShaneAu on 2006-04-18
I get this error when I try to access any things that would normally require a root password to be entered to access them, and I cannot get into terminal (it says it's load in the taskbar and then just goes away and nothing is loaded) or log into my system via SSH (server unexpectedly closed network connection).

I've attached a screenshot of the error I get to this post.

I think this happen after it downloaded and installed the latest Kernel, I avoid rebooting my box at all costs, I don't care about booting into the latest Kernel, I'm just on a mission to see how high I can get the uptime. :p

---

### Post by Miguel on 2006-04-18
What happens if you change to tty1 and login from there?

By default, ubuntu loads 7 terminals: 6 cli and the X session. You can change to one of these by pressing Ctrl+Alt+Fx (where x goes from 1 to 7, and 7 sends you back to X). Can you login from one of these? Will "sudo -i" make you root?

---

### Post by ShaneAu on 2006-04-25
I get "sudo: Can't open /var/run/sudo/shane/tty1: Read only file system" when I try "sudo -i" and input the root password.

---

### Post by Miguel on 2006-04-25
It seems like a permission problem in /etc/fstab. If you issue a "cat /etc/fstab" (you needn't use sudo or whatever), what is the result?. Please note that you will probably need a live CD or a reinstall to fix this.

BTW: My fstab looks like this:
```

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /fat32          vfat    defaults,uid=1000,gid=100,dmask=0000,fmask=0113     0       0
/dev/hda6       /home           ext3    user_xattr      0       2
/dev/hda1       /media/windows  ntfs    defaults,dmask=0222,fmask=0333        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by ShaneAu on 2006-04-25
Well I attempted a reboot, but there are problems.

I get "Error 25" on the Grub Loader.

I've tried a few things mentioned on these forums about this "error 25" but havn't been able to fix it.

It's not looking good.

---

### Post by Miguel on 2006-04-25
Alright, a few things:[list]
[*] When you rebooted, at what stage did grub stop? It is listed in top of the error. It can be, at least, stage 1, stage 1.5 and stage 2.
[*] Do you have a live-cd at hand? Knoppix or Ubuntu or whatever
[*] Once you have access to your system (i.e. via a live CD), please post the output (root power needed) of 
```
$ fdiks -l /dev/hda (sda if you have a SATA disk)
```
[*] Then, mount the / partition (or /boot and /etc). We need to read the content of /boot/grub/menu.lst and /etc/fstab
[/list]

You will have to use the "root terminal" of the live CD. I think this could be solvable withouth reinstalling. Just in case, remember that you can still recover your data, so don't despair.

---

### Post by ShaneAu on 2006-04-26
[QUOTE=Miguel]Alright, a few things:[list]
[*] When you rebooted, at what stage did grub stop? It is listed in top of the error. It can be, at least, stage 1, stage 1.5 and stage 2.
[*] Do you have a live-cd at hand? Knoppix or Ubuntu or whatever
[*] Once you have access to your system (i.e. via a live CD), please post the output (root power needed) of 
```
$ fdiks -l /dev/hda (sda if you have a SATA disk)
```
[*] Then, mount the / partition (or /boot and /etc). We need to read the content of /boot/grub/menu.lst and /etc/fstab
[/list]

You will have to use the "root terminal" of the live CD. I think this could be solvable withouth reinstalling. Just in case, remember that you can still recover your data, so don't despair.[/QUOTE]
Ok, it's on stage 1.5.
I do have a Live-CD, Ubuntu 5.04.

Output of fdisk (I think that's what you wanted, not fdiks):
```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device		boot	start	end	blocks		id	system
/dev/hda1	*	1	9541	76638051	83	Linux
/dev/hda2		9542	9729	1510110		5	Extended
/dev/hda5		9542	9729	1510078+	82	Linux swap/ Solaris

```

Then how do I mount the partiton I need? / I'm guessing.

It says:

The standard form of the mount command, is:
mount -t type device dir

From that, I try this:
```

mount -t ext3 /dev/hda ./sparky

```

Where "sparky" is a directory I made for it. I get this output:

```

mount: /dev/hda already mounted or ./sparky busy

```

Then I try this:

```

mount -t ext3 /dev/hda1 ./sparky

```

The output is:

```

mount: wrong fs type, bad option, bad superblock on /dev/hda1,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

```

And yes, I'm at / on the live CD where the "sparky" directory is.

In syslog I see:

```

hda: dma_intr: status=0x51 { DriveRead SeekComplete Error }
hda: dma_intr: error=0x40 { UncorrectableError ], LBAsect=127, high=0, low=127, sector=127
ide: failed opcode was: unknown
end_request: I/0 error, dev hda, sectory 127
EXT3-fs error (device hda1): ext3_get_inode_loc: unable to read inode block - inode=8, block=8
EXT3-fs: invalid journal inode.

```

I wrote all that by hand, so there may be a few typos. I hope I can get this fixed. :(

I don't understand how it can just stop working all of a sudden, after 185 days of working fine non-stop.

Thanks for your help so far, Miguel. :)

---

### Post by Miguel on 2006-04-26
I'll have a look at grub, but more of that later. I've had a meeting with my thesis director and have another commission meeting in 20 minutes. However, those error messages don't look nice at all.

First, the bad news. Unless you are using anything other than ext3, I suspect that maybe your HD has failed. It's just a maybe, though. After mounting a partition (/dev/hda**x**, without a number it refers to the whole HD), could you issue the following?
```

$ dmesg | tail -20

```
This should be identical, but will show the last 20 lines instead. 

**Note:** You needn't copy all the output by hand. You can highlight the output with the mouse and, withouth closing the terminal, middle-click in another window will automatically copy-paste the highlighted text... for example in Firefox.

**Note 2:** If you don't have a 3 button or a wheel mouse, the third button is emulated by pressing both buttons at once.

But let's go on. Like Lenny Kravitx's song, "It ain't over till it's over". First, try mounting again your partition without specifiying the FS, that is, without "-t ext3". This might work, because mount attempts to autodetect the FS type, and can succeed in many cases. If the partition with your data is ext3, you can try mounting it as ext2. It will work, with the exception of the journaling of ext3.

I'm on a hurry. See you later.

---

### Post by ShaneAu on 2006-04-26
[QUOTE=Miguel]I'll have a look at grub, but more of that later. I've had a meeting with my thesis director and have another commission meeting in 20 minutes. However, those error messages don't look nice at all.

First, the bad news. Unless you are using anything other than ext3, I suspect that maybe your HD has failed. It's just a maybe, though. After mounting a partition (/dev/hda**x**, without a number it refers to the whole HD), could you issue the following?
```

$ dmesg | tail -20

```
This should be identical, but will show the last 20 lines instead. 

**Note:** You needn't copy all the output by hand. You can highlight the output with the mouse and, withouth closing the terminal, middle-click in another window will automatically copy-paste the highlighted text... for example in Firefox.

**Note 2:** If you don't have a 3 button or a wheel mouse, the third button is emulated by pressing both buttons at once.

But let's go on. Like Lenny Kravitx's song, "It ain't over till it's over". First, try mounting again your partition without specifiying the FS, that is, without "-t ext3". This might work, because mount attempts to autodetect the FS type, and can succeed in many cases. If the partition with your data is ext3, you can try mounting it as ext2. It will work, with the exception of the journaling of ext3.

I'm on a hurry. See you later.[/QUOTE]
I get the same errors as I posted above.

I think I might just try to focus on trying to recover data now, :(. Is it possible?

Thanks.

---

### Post by Miguel on 2006-04-27
I am really sorry to post this. It seems that your HD has an error somewhere. And it seems important enough not to allow mounting the partition. I don't know enough to help you recover your files. 

If no one else knows the answer, maybe resizing the partition a few megs (with gparted on the live cd) might help. But this is a desperate attempt, as it could corrupt all the data on your HD.

Does anybody here know how to help save Shane's data?

---

### Post by ShaneAu on 2006-04-29
[QUOTE=Miguel]I am really sorry to post this. It seems that your HD has an error somewhere. And it seems important enough not to allow mounting the partition. I don't know enough to help you recover your files. 

If no one else knows the answer, maybe resizing the partition a few megs (with gparted on the live cd) might help. But this is a desperate attempt, as it could corrupt all the data on your HD.

Does anybody here know how to help save Shane's data?[/QUOTE]

Ok, yes, it sucks that this has happened, there were many family photos stored on it, there must be a way to recover the data - somehow (*Hint, hint. Anyone know? :().

I appreciate your help very much Miguel, thanks again.

The hard drive should be still under warranty, so I don't mind about that, just getting them photos back is most important to me.

---

