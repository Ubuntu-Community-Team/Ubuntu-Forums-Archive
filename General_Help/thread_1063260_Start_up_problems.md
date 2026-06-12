---
title: "Start up problems"
date: 2009-02-07
forum: General Help
---

### Post by rweaver4 on 2009-02-07
After many attempts I have managed to install Ubuntu 8.10 and I have dual booting with Windows XP.


I have used 'Start up Manager', but find that the XP installation on a partition on the same disk as the Ubuntu partition is not listed as a start up option. The other XP installation on a separate disk is listed.

I have reduced the delay time to 1 sec but find that the time to start up any of my options now takes nearly 5 minutes instead of the previous 20 secs.

Also after taking 5 minutes to open, Ubuntu then does what appears to be a memtest or system check before starting and I can find no instruction causing this.

Any solutions welcome,

Thanks,

Robert.

---

### Post by kayvortex on 2009-02-07
The settings for grub are stored in the file "/boot/grub/menu.lst". Could you please post the contents of that file.

If you know what partitions your various file systems are on, could you also state that. If not, then could you enter:
```
sudo fdisk -l *disk*
```
where "disk" is the name of your disk for each of them on your system (/dev/sda or /dev/hda, or /dev/sdb, /dev/sdc...).

---

### Post by rweaver4 on 2009-02-07
Thanks, I can't do that immediately as I am working on the XP. I will post as soon as possible and am looking forward to your help.
Robert

---

### Post by rweaver4 on 2009-02-07
Here are the disks, Disk 0 containd Windows XP home and Ubuntu 8.10, Disk 1 contains XP pro. XP home does not appear in grub options.

---

### Post by rweaver4 on 2009-02-08
THis doesn't look good:

weaver00@study:~$ sudo /boot/grub/menu.lst
/boot/grub/menu.lst: 14: default: not found
/boot/grub/menu.lst: 126: title: not found
/boot/grub/menu.lst: 127: uuid: not found
/boot/grub/menu.lst: 128: kernel: not found
/boot/grub/menu.lst: 129: initrd: not found
/boot/grub/menu.lst: 130: quiet: not found
/boot/grub/menu.lst: 132: Syntax error: "(" unexpected

weaver00@study:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe44ee44e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

weaver00@study:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed6ced6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       25865   207760581    7  HPFS/NTFS
/dev/sdb2           25866       38913   104808060    5  Extended
/dev/sdb5           25866       38377   100502608+  83  Linux
/dev/sdb6           38378       38913     4305388+  82  Linux swap / Solaris
weaver00@study:~$ 

When grub loads, the boot menu gives me these options to choose from:

Ubuntu 8.10, kernel 2.6.27-11-generic

Ubuntu 8.10, kernel 2.6.27-11-generic (Recovery Mode)

Windows NT/2000/XP (Loader)

Microsoft Windows XP professional

Windows NT/2000/XP (Loader)

Last used

Windows XP Home is on the partition on the same disk as Ubuntu, but is not on this list. If I go to 
Windows NT/2000/XP (Loader) I get the choice of the two Windows options.

Any suggestions?



I hope this is what you are requesting?

---

### Post by mb_webguy on 2009-02-08
He was asking for the contents of the menu.list file.  To edit the file, you would use "gksu gedit /boot/grub/menu.list", but to display the contents, you can use "cat /boot/grub/menu.list".

---

### Post by rweaver4 on 2009-02-08
I apologise for my newbie ignorance but what you suggested gives me this:

weaver00@study:~$ cat/boot/grub/menu.lst
bash: cat/boot/grub/menu.lst: No such file or directory

?

---

### Post by rweaver4 on 2009-02-08
However I got this from the editing input, note there is no reference to Windows XP Home which is on the same disk as Ubuntu:-

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		efb31d69-870b-45a6-b03c-082f3d4bab50
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=efb31d69-870b-45a6-b03c-082f3d4bab50 ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		efb31d69-870b-45a6-b03c-082f3d4bab50
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=efb31d69-870b-45a6-b03c-082f3d4bab50 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sde1
title		Windows NT/2000/XP (loader)
root		(hd3,0)
savedefault
makeactive
map		(hd0) (hd3)
map		(hd3) (hd0)
chainloader	+1

---

### Post by kayvortex on 2009-02-08
Well, for one thing, in that last option
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sde1
...
root (hd3,0)
you don't have a fourth disk; and you certainly don't have an sde1 partition.

From this mistake, and your general problems booting, I'd think that there are just incorrect entries in your menu.lst file. Now, there are two things you could do: the first is simply to run through the file and correct any mistakes and make modifications to pinpoint where the problem is. Some of the things you could do include remove the "splash" in
> kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=efb31d69-870b-45a6-b03c-082f3d4bab50 ro quiet splash vga=791
and then you'll be able to see what the system is doing when it is booting. You could also replace the "uuid" commands with "root" commands so that you know what partition it is you're trying to boot.
**However**, I personally find that in these situations it is *far* easier to simply reinstall grub: it's not difficult at all and very often solves the problem at the first attempt.

If you really want to know what/how/why your booting procedure has gone wrong, I'll try my best to help you go through it; but if you just want to try to fix the problem right now, then take a look at this to reinstall grub:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

It runs through everything that you have to do quite clearly and I used it myself when I had problems booting back when I didn't know much about grub and booting (although I still don't, really!).
**First, though**, backup your current menu.lst file:
```
sudo cp -i /boot/grub/menu.lst /boot/grub/menu.lst.my-backup
```
Then, read the first few posts of that topic because it will give you an alternative procedure if the first one doesn't work.
If you still have problems, or don't quite understand what to do, post back here your problems/concerns and I'll be happy to help.
Good luck!

---

### Post by 3rdalbum on 2009-02-08
PLEASE copy and paste the commands from the forum into your terminal window rather than retyping them. You've mistyped a couple of them now :-)

Quick terminal basics: The terminal is actually just a way of running programs. Each terminal command runs a program (whose name is the first word) and then the next bits of the command are just information that you are providing the program. If you put "sudo" before a command, it runs it as the administrator.

The command you were asked to put is:

```
cat /boot/grub/menu.lst
```

So, "cat" is the program, and /boot/grub/menu.lst is the information you are providing to the program - in this case, the path of a file to read.

Hope this helps you understand the commands that you'll get asked to run :-)

---

### Post by rweaver4 on 2009-02-08
Many thanks to all who have helped me with this problem. After studying your advice, I have boldly ( as a newbie) edited the grub menu which now looks like this:-


title		Ubuntu 8.10, kernel 2.6.27-11-generic 
uuid		efb31d69-870b-45a6-b03c-082f3d4bab50 
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=efb31d69-870b-45a6-b03c-082f3d4bab50 ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.27-11-generic 
quiet 

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) 
uuid		efb31d69-870b-45a6-b03c-082f3d4bab50 
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=efb31d69-870b-45a6-b03c-082f3d4bab50 ro  single 
initrd		/boot/initrd.img-2.6.27-11-generic 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 
root 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda1 
title		Windows XP Home 
root		(hd0,0) 
savedefault 
makeactive 
chainloader	+1 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sdb1 
title		Microsoft Windows XP Professional 
root		(hd1,0) 
savedefault 
makeactive 
map		(hd0) (hd1) 
map		(hd1) (hd0) 
chainloader	+1 



I am now able to set grub to automatically boot to any of the operating systems.
I also discovered that the removal of a usb 8gb memory stick stopped the disk checking and reduced the start up time.
Thanks again,

Robert

---

