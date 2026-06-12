---
title: "Grub loading please wait...."
date: 2009-05-24
forum: General Help
---

### Post by eeyore357 on 2009-05-24
This has happened to me 3 times now. I can restart my computer a few times after a new install then "Grub loading please wait" and it just stalls there without any error. I have noticed that my floppy drive makes a sound like it is searching for a disc and the light stays on. I finally made the switch from that other OS and really like Linux except for this problem... Does anyone know how I can fix this?

---

### Post by colau on 2009-05-24
Be specific please.
So you can't access any operating system?
Are you using windows xp with ubuntu?

---

### Post by colau on 2009-05-24
Be specific please.
So you can't access any operating system?
Are you using windows xp with ubuntu?

---

### Post by eeyore357 on 2009-05-24
I only have Ubuntu installed..  *Grub loading* Stage1.5 *Grub loading*, *please wait  [I]This has happened with the newest ver*.[I] of Ubuntu and the one before it. I have been searching the internet for an answer and on another post someone sugested hitting esc when grub is loading. I was able to get to a screen where you can chose the device to boot. One of my secondary hard drives was listed by name. I selected scsi/ata100 as that is my primary HD. Same error.... 
[/I][/I]

---

### Post by Legace on 2009-05-24
Try to disable your floppy drive in BIOS..

---

### Post by eeyore357 on 2009-05-24
I disabled the floppy... same problem but the light on the drive doesn't stay on.

---

### Post by eeyore357 on 2009-05-24
My computer setup
Asus A7V
768Mb PC-133
AMD Duron 1300
Samsung 40GB (main drive)
Maxtor 40GB (backup)
Freeagent 300GB (usb drive)
Sony DVD-RW
Nvidia AGP 128MB
ect..

---

### Post by moshuptrail on 2009-05-24
Check the HD for bad blocks.

---

### Post by eeyore357 on 2009-05-24
HD is good.. I tried deleting all stage1_5 files and doing this process
1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,0)".

6. Type "setup (hd0,0)". and  "setup (hd0)"

7. Type "quit".

Now I get to "Grub loading stage 2"  Should I try deleting stage2 files and doing that again?

---

### Post by VMC on 2009-05-24
From Applications > Accessories > Terminal, type the following so we know what we're dealing with:

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by eeyore357 on 2009-05-24
[guest@localhost ~]$ sudo fdisk -l
bash: sudo: command not found
[guest@localhost ~]$ su
[root@localhost guest]# fdisk -l

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a377a37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4665    37471581   83  Linux
/dev/sda2            4666        4870     1646662+   5  Extended
/dev/sda5            4666        4870     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd6190175

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4982    40017883+   c  W95 FAT32 (LBA)

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       38913   312568641    7  HPFS/NTFS

I couldn't get cat /boot/......   to work.
[root@localhost guest]# cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
[root@localhost guest]# fdisk -l cat /boot/grub/menu.lst
[root@localhost guest]#

---

### Post by VMC on 2009-05-24
Try this from that Terminal:

```
uname -a
```

also, see if this works

```
df -T
```

Finally see if you can go here

```
cd /boot/grub
```

if so then "list the contents:

```
ls
```

---

### Post by eeyore357 on 2009-05-24
I can open the menu.lst file from the file manager is there any specific info you need from it?

---

### Post by eeyore357 on 2009-05-24
[root@localhost guest]# uname -a
Linux localhost 2.6.27-desktop586-0.rc8.2mnb #1 SMP Thu Oct 2 05:52:21 EDT 2008i686 AMD Duron(tm) Processor GNU/Linux
[root@localhost guest]# df -T
Filesystem    Type    Size  Used Avail Use% Mounted on
none       unionfs    379M   31M  348M   9% /
/dev/sda1     ext3     36G   13G   21G  38% /media/hd
/dev/sdb1     vfat     39G   30G  9.0G  77% /media/hd2
[root@localhost guest]# cd /boot/grub
[root@localhost grub]# ls
menu.lst.example
[root@localhost grub]#

---

### Post by VMC on 2009-05-24
> **eeyore357 said:**
> HD is good.. I tried deleting all stage1_5 files and doing this process
1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,0)".

6. Type "setup (hd0,0)". and  "setup (hd0)"

7. Type "quit".

Now I get to "Grub loading stage 2"  Should I try deleting stage2 files and doing that again?

Why did you start deleting files in the grub folder?
Type the following and see what , if anything appears:

```
find /boot/grub/stage1
```

---

### Post by eeyore357 on 2009-05-24
grub> find /boot/grub/stage1
 (hd0,0)

It was one of the suggestions in another forum and worked for someone. What I have read says stage1_5 is optional and can be deleted.

---

### Post by eeyore357 on 2009-05-29
bump :(

---

