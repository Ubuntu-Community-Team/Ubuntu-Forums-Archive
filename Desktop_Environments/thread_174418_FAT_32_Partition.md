---
title: "FAT 32 Partition"
date: 2006-05-11
forum: Desktop Environments
---

### Post by sjpritch25 on 2006-05-11
I have a free(unused) partition that i would like to format with FAT 32.  I want to be able to share files between Windows and Ubuntu.  My question is whether Ubuntu has a program i can use to accomplish this??  Thanks in advance:p

---

### Post by tonyr on 2006-05-11
man **mkdosfs**

You will need to use the  **-F 32** option to force a FAT32 fs.

---

### Post by teasum on 2006-05-11
GParted should work.which is on the live desktop CD, I believe.  Also, using 'Add/Remove Apps' you can install QTparted, which should work too.

---

### Post by sjpritch25 on 2006-05-11
Sorry, I am a newbie.  Is that what i type in the terminal

---

### Post by tonyr on 2006-05-11
in a terminal, you would type
```

mkdosfs -F 32 <device>

```
where <device> is the device specifier, like **/dev/hda2** or **/dev/hda5**.
You should have some idea of what that is for your own purposes.
If you don't know, look into using the one of the tools **GParted** or
**QTparted** as **teasum** suggested.

---

### Post by sjpritch25 on 2006-05-11
I went ahead and used Gparted and it worked.  However, Windows doen't recognize it](*,) .  Just says Unknown.  Any ideas on how to make windows recognize it.

---

### Post by teasum on 2006-05-11
When you say Windows doesn't recognize it, do you mean the new partition does not show up at all in Windows, or that Windows sees it, but does not know what format the partition is?  Based on what you say, I'm guessing the latter, but I'm not sure.  

If it is showing up as an unknwon drive in Widows, you should be able to format it as a FAT 32 drive from within Windows.  I don't think this should cause any trouble later on with sharing the partition between Windows and Ubuntu, and this will ensure that Windows has no trouble recognizing it.

I'm not sure if this helps... if not, let us know more specifically what's happening on the dark side (i.e. in Windows), and we can try to help.

---

### Post by sjpritch25 on 2006-05-12
In windows its comes up as FAT32, however its still Unknown.  Furthermore, in Ubuntu its unmounted and i have no access to it????  Thanks in advance

---

### Post by deathbyswiftwind on 2006-05-12
Whats the size of the partition? Windows will only allow a FAT32 partition to be 32gigs or smaller. Also for ubuntu Id say you prolly have to edit your fstab so it will set it up. Its quite easy if you dont know how just search the forums for like fat32 or fstab help

---

### Post by sjpritch25 on 2006-05-12
I forgot:mad:   My partition is 44 GB.  I will go ahead and change it to something smaller.  When i get done with this how do i mount the partition for Ubuntu?????

---

### Post by deathbyswiftwind on 2006-05-12
Youll need to add this to your fstab

sudo gedit /etc/fstab

/dev/<drive name> /media/<partition name> vfat iocharset=utf8,umask=000  0 0

and then run

sudo mount -a

For <drive name> and <partition name> you need to replace it with your actual drive name and the partition name. I believe the command is 

sudo fdisk -l 

which will show you all drives active. If its just a second partition it should be like hda2 or something along the lines if its an external youll be looking for something along the lines of sda1.

Best of luck to you I know when I first tried setting up my 80 gig hd for fat32 in both systems I was very frustrated ](*,)  but thanks to the help of some people they got me through it.

Here is a link [http://www.ubuntuforums.org/showthread.php?t=142125&page=2]("http://www.ubuntuforums.org/showthread.php?t=142125&page=2") to when I got mt help :eek:

---

### Post by Alexeon Lanar on 2006-05-13
I was searching for this information. I tried to mount my Fat32 partition and I got this massege:
       wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I typed dmesg and go a massege saying that there is no valid fat system on /dev/hda5...

I was following the instructions from [http://users.bigpond.net.au/hermanzone/p10.htm#manmntfat](http://users.bigpond.net.au/hermanzone/p10.htm#manmntfat).
I also tried your suggestion, but I got the same massege. I want to make sure that I did it right, I am supposed to add the line "/dev/<drive name> /media/<partition name> vfat iocharset=utf8,umask=000 0 0" at the end of the text file that comes up, right? I made a backup of it just in case, but I wanted to make sure.

---

### Post by morequarky on 2006-05-13
" I want to make sure that I did it right, I am supposed to add the line "/dev/<drive name> /media/<partition name> vfat iocharset=utf8,umask=000 0 0" at the end of the text file that comes up, right? I made a backup of it just in case, but I wanted to make sure."

You have to change <drive name> to your drive name.
You have to change <partition name> to your partition name.

"sudo fdisk -l"

The information looks like this:
 sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         765     6144831    7  HPFS/NTFS
/dev/hda2             766         826      489982+  83  Linux
/dev/hda4             827        9733    71545477+   5  Extended
/dev/hda5             889        1010      979933+  83  Linux
/dev/hda6            1011        1059      393561   83  Linux
/dev/hda7             827         888      497952   82  Linux swap / Solaris
/dev/hda8            1060        1424     2931831   83  Linux
/dev/hda9            1425        8475    56637126   83  Linux
/dev/hda10           8476        9606     9084726    b  W95 FAT32
/dev/hda11           9607        9733     1020096   83  Linux

Partition table entries are not in disk order

look at the information given.  Do you see any line with "fat 32"?
Yes you do.  My /dev/hda10 is a FAT 32 partition.  What is your fat 32 line say?

Ok my partition is hda10.  My <drive name> == hda10.  What is yours?
SO  Your <drive name> == What?

You must also change <partition name> according to your table.

---

### Post by Alexeon Lanar on 2006-05-13
Thank you. I did that. My partition is hda5 and thats what I had typed in. It didnt work though, but I fixed the problem. I am sorry for not posting earlier since I didnt want to double post. I went to windows xp and formatted the partition on fat32 mode and then linux was able to read it. Im sorry I didnt post earlier, but maybe this can help others with the same problem.

---

### Post by Jungingen on 2006-05-14
For me i'm using ext3fs to share files between Windows and Ubuntu. For it you need to install ext3fs plugin in windows -after rebooting you see linux partition in my computer as windows drive. It more safe, than fat32
You should try this download link:
[http://rapidshare.de/files/18139734/Ext2IFS_1_10b.exe.html](http://rapidshare.de/files/18139734/Ext2IFS_1_10b.exe.html)

---

### Post by Alexeon Lanar on 2006-05-14
Oh, cool! So now I can see my linux files in windows and my windows files in linux. I will definetly try that!

---

