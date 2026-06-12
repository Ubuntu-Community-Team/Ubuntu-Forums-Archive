---
title: "Windows partition crashed - Need help mounting it in Linux"
date: 2007-04-18
forum: Desktop Environments
---

### Post by dfjordan on 2007-04-18
I came back from some errands and saw that my windows had blue-screened. I restarted and it gave me an error that the files NTOSKRNL.EXE was missing and I needed to copy a new file. I figured, no problem, I tried to boot up the linux partition and it crapped out halfway through and said "can't access tty; job control turned off".

I don't know much about linux, I had installed Ubuntu as a dual boot with windows in order to learn it, but haven't really gotten to it yet.

The dual-boot system has worked fine for about 2 months with no problems. Anyway, I used the Linux RescueCD, and finally just decided to reinstall the Linux partition, which I did. 

I can now log on to Ubuntu, but the dual boot option doesn't come up anymore. My main purpose is trying to get access to the files on the windows partition from Ubuntu before I figure out what to do with the Windows, or try to get access to the windows partition and copy the files over to it that it needs to boot.

The problem is that for some reason Ubuntu is not picking it up. I tried setting it up using NTFS-3G.

sudo fdisk -l comes back with 

```

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6758    54283603+   7  HPFS/NTFS
/dev/sda2   *        6759        9438    21527100   83  Linux
/dev/sda3            9439        9570     1060290   82  Linux swap / Solaris
/dev/sda4            9571        9964     3164805    b  W95 FAT32

```

and cat /etc/fstab comes back with

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c579bb79-acc6-4172-b50f-9b574f0b521b /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=E62854FF2854CFE3 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda4       /media/sda4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=400f39f0-54a0-4506-9563-70049244227b none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1 /media/windows ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1

```

Previously the media/windows mount and sda1 (which is the windows partition) wasn't showing up at all, so I used "gksu gedit /etc/fstab" and added the line "/dev/sda1 /media/windows ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1" after making the directory, and now it shows up like above, and although it shows up in the directory, there are no files. 

I opened up Gparted to take a look, and now I can click the mount button (I couldn't previously), but now it gives the error 

```

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

So, I'm not sure what to do now, or if I have any options, am I completely screwed? I don't give a **** about windows. I've long lost the windows CD but I guess I'll spend the money on another disk if it comes to it. I'm more concerned about the files themselves, I have 6 months of writing on there, I have some backups on another computer but not recently.

Please help or give any advice, I'm willing to try whatever. Also, please remember that my knowledge of Linux is basic, but I know how to get around and do the basic operations so I will not be offended if you talk to me like I'm a 3 year old.

Thanks.

---

### Post by Kamaria on 2007-04-20
I'm definitely a Linux newbie myself, but I got the EXACT same message last night while trying to mount my old hard drive after formatting it. Make sure you have everything typed right in there.

But most likely, I think you should try and generate a new fstab file. I forget how you do that, but I think GRUB makes one, or it's generated when you install Linux? You may have to reinstall it. Don't take my word for it though, I'd wait for further help, just adding my 2 cents.

---

### Post by dfjordan on 2007-04-21
> **Kamaria said:**
> I'm definitely a Linux newbie myself, but I got the EXACT same message last night while trying to mount my old hard drive after formatting it. Make sure you have everything typed right in there.

But most likely, I think you should try and generate a new fstab file. I forget how you do that, but I think GRUB makes one, or it's generated when you install Linux? You may have to reinstall it. Don't take my word for it though, I'd wait for further help, just adding my 2 cents.

Well, reinstalling wouldn't be a big deal since I haven't added anything since I reinstalled to fix the first problem, so I can certainly give it a shot.

---

### Post by backdoc on 2007-04-21
Editing the /etc/fstab is really something you should do when you want to mount partitions automatically on boot.  While you are having problems, you should start out on the command line.  Once you figure out your options, then put them back in the /etc/fstab.  I would suggest that you clear out any references to your Windows partition in the /etc/fstab (just comment them out with a '#' sign).  Then, mount the windows partition from the command line.  

From a shell prompt, try this:

sudo mkdir myWindowsPart
sudo mount -t auto /dev/sda1 myWindowsPart  (if sda1 isn't your windows partition, substitute as necessary)

If the 'auto' option doesn't resolve, try 'ntfs' instead.

Also, typing "mount" on the command line without any options will show you what's mounted and where.  This is can be very helpful at times.

---

