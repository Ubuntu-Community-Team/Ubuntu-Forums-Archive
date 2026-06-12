---
title: "Can't find partitions! Probable problem with MBR or similar"
date: 2009-02-22
forum: General Help
---

### Post by Ederico on 2009-02-22
Unfortunately I seem to have done something to the MBR or the partition table without intending.

I guess this all started when I used GParted to eliminate my Ubuntu partition and merge the space to my Kubuntu partition. Eventually this led me end up with no primary partition and having all partitions in the extended partition as logical partitions.

I then eventually tried loading up my Windows XP partition and this gave me problems (didn't load at all). I tried using Super Grub Disk to fix the situation but it just got worse, the bootloader is just gone completely and that isn't loading at all. Worse still, Super Grub Disk is not succeeding in installing GRUB again and I can't even load Kubuntu or Windows directly from it.

And, using GParted I just get one whole block of "unallocated space" without any partitions at all.

This sounds bad, I would appreciate if anyone could tell me how to fix this problem or at least how to recover my data (luckily I should have some recent backups if all comes to worse). If this can't be done, oh well I'll have to reinstall everything from scratch.

Thanksb beforehand.

Ederico.

---

### Post by Herman on 2009-02-22
You should be able to use [COLOR=#C0C0C0][TestDisk - CG Security]("http://www.cgsecurity.org/wiki/TestDisk") [/COLOR]to fix your partition table, there is good documentation at the TestDisk website to show you how, [TestDisk Step by Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step").
Good luck with it.
Regards, Herman :)
[COLOR=#C0C0C0] [/COLOR]

---

### Post by Ederico on 2009-02-22
Ok, using TestDisk changed the situation in GParted, but I'm shown the partitions as they were before I did the operation listed in my post, as if I had done nothing. In fact I did, so much so that in TestDisk the partitions are shown correctly.

EDIT - Actually, in TestDisk the situation is identical. I'm shown a partition which I had deleted and the space of which I merged into the other Linux partition. I think the problem is because I deleted my primary partition ending up with no primary partitions, this is what I need fixed.

---

### Post by caljohnsmith on 2009-02-22
So have you fixed your partition table with testdisk yet? If you haven't yet, how about posting:
```
sudo fdisk -lu
sudo sfdisk -d
```
Also, when you use testdisk, I would strongly recommend using the "deeper search" feature, because the "quick search" results are often not accurate about finding all the valid partitions. What version of testdisk are you using? If you are using a version prior to 6.10, I would recommend downloading the 6.10 version and using that, because it has some important bug fixes that the previous versions don't have. If you download the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop, you can run it with:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
To do a "Deeper Search" with testdisk, you can follow these directions: after starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and also which of those partitions seem to be the partitions you want to recover. We can work from there if you want.

---

### Post by Ederico on 2009-02-22
Ok, I'm using TestDisk 6.4 through my GParted Live CD. Unfortunately I do not have any Ubuntu/Kubuntu LiveCDs with me and even worse I have no working CD-Writer or similar, except the laptop one which has no working OS.

I ran fdisk -lu and I got:

```
DEVICE BOOT START END BLOCKS ID SYSTEM
/dev/sda1 * 63 83955689 41977813+ 83 Linux
/dev/sda2   84855330 117194174 16169422+ 7 HPFS/NTFS
```

I ran sfdisk -d and I got:

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start= 63, size= 83955627, Id=83, bootable
/dev/sda2 : start= 84855330, size= 32338845, Id= 7
/dev/sda3 : start= 0, size= 0, Id= 0
/dev/sda4 : start= 0, size= 0, Id= 0
```

Now, I would live to able to run a live version of Kubuntu through a USB drive (my only option given the circumstances), and I followed the tutorial found [here]("http://www.tomas.cat/blog/en/using-kubuntu-810-usb-device-flash-drive-hard-drive") but in the Windows Command Prompt when I tried the last command I got:

> Reading boot sector: The parameter is incorrect

---

### Post by Ederico on 2009-02-22
By the way, through TestDisk I actually installed its boot option (which gives the 1234F at startup) and when I press 1 for Linux nothing happens, when I press 2 for Win XP it starts loading but it basically stop at the Windows loading page. I tried something else and I'm getting:

```
NTLDR is missing
Press any key to restart
```

---

### Post by Ederico on 2009-02-22
When I run a deep search I get the following:

```

PARTITION START END SIZE IN SECTORS

D FAT12 0 1 1 1 254 63 32067 [NO NAME]
D Linux 0 1 1 5225 254 63 83955627
D Linux 4104 1 1 5225 254 63 18024867
L Linux Swap 5226 1 1 5281 254 63 899577
* HPFS - NTFS 5282 0 1 7294 254 63 32338845
```

---

### Post by caljohnsmith on 2009-02-22
> **Ederico said:**
> When I run a deep search I get the following:

```

PARTITION START END SIZE IN SECTORS

[COLOR="Red"]D[/COLOR] FAT12 0 1 1 1 254 63 32067 [NO NAME]
[COLOR="Red"]P[/COLOR] Linux 0 1 1 5225 254 63 83955627
[COLOR="Red"]D[/COLOR] Linux 4104 1 1 5225 254 63 18024867
[COLOR="Red"]P[/COLOR] Linux Swap 5226 1 1 5281 254 63 899577
[COLOR="Red"]*[/COLOR] HPFS - NTFS 5282 0 1 7294 254 63 32338845
```
The first Linux partition above looks like it is exactly the same as the one fdisk currently lists, and same is true about the NTFS partition above. So about the only extra partition you can recover would be your swap partition. I would recommend marking the first linux partition and the swap partition as "P", and then mark NTFS partition with "*" like it is. Then you can write that partition table and you'll have your swap partition back at least, but I don't know what that will accomplish until you can get a Live CD booting on your computer.

---

### Post by Ederico on 2009-02-22
I managed to get an Ubuntu Live CD, the data in the Windows partition seems to be fine even if booting Windows is still problematic. However, the Kubuntu partition is showing definite problems. Check screenshot.

EDIT: I did what you instructed in the previous post before using the Live CD.

---

### Post by caljohnsmith on 2009-02-22
How about posting:
```
sudo fdisk -lu
```
Find which is the kubuntu partition, for example sda1, and then do:
```
sudo umount /dev/[COLOR="Blue"]sda1[/COLOR]
[[ $(mount | grep [COLOR="Blue"]sda1[/COLOR]) ]] || sudo e2fsck -fpv /dev/[COLOR="Blue"]sda1[/COLOR]
```
Replace sda1 with the kubuntu partition, and post the output of the above commands so I can see what fsck says about the kubuntu partition.

---

### Post by Ederico on 2009-02-22
```
/dev/sda1              63    83955689    41977813+  83  Linux
/dev/sda2        83955690    84855329      449820    f  W95 Ext'd (LBA)
/dev/sda3   *    84855330   117194174    16169422+   7  HPFS/NTFS
/dev/sda5        83955753    84855329      449788+  82  Linux swap / Solaris

```

Right now I'm running testdisk 6.10 as well, doing a deep search. I'll post the results as soon as it is done. I'll try the second instruction in your last post.

(And no matter what, thanks a lot for the help!)

---

### Post by Ederico on 2009-02-22
Here's the result for the second instruction:

```
/dev/sda1: Inode 50277 has EXTENTS_FL flag set on filesystem without extents support.


/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)

```


And here are the results running a deep search with testdisk 6.10:

```
Disk /dev/sda - 60 GB / 55 GiB - CHS 7296 255 63
     Partition               Start        End    Size in sectors
D FAT12                    0   1  1     1 254 63      32067 [NO NAME]
D Linux                    0   1  1  5225 254 63   83955627
D Linux                 4104   1  1  5225 254 63   18024867
L Linux Swap            5226   1  1  5281 254 63     899577
* HPFS - NTFS           5282   0  1  7294 254 63   32338845

```

---

### Post by caljohnsmith on 2009-02-22
In the testdisk results you posted, if you select each of the two linux partitions and press "p" to get a directory listing, does that successfully show you a directory listing for either partition?

---

### Post by Ederico on 2009-02-22
I do get a directory listing and till there it all seems fine, however trying to access my directory and the home directory doesn't seem to show the directories that should be there or any files.

---

### Post by caljohnsmith on 2009-02-22
> **Ederico said:**
> I do get a directory listing and till there it all seems fine, however trying to access my directory and the home directory doesn't seem to show the directories that should be there or any files.
OK, but which partition gives you the directory listing? Is it the first linux partition?

---

### Post by Ederico on 2009-02-22
Actually, both do but when I try accessing my directory in the home directory the results are different. The first one just seems empty, the second one says that the filesystem is damaged.

---

### Post by caljohnsmith on 2009-02-22
Is your Kubuntu partition supposed to start at the beginning of the drive? If so, the first linux partition in the deep search results would be the valid one, and that's the one you've all ready recovered when you were using the older testdisk.

---

### Post by Ederico on 2009-02-22
It is supposed to be there, but it wasn't. The first Linux partition was running Ubuntu, but I had deleted that and then I made the Kubuntu partition the first using testdisk.

---

### Post by caljohnsmith on 2009-02-22
OK, well the bottom line is I think testdisk recovered your correct Kubuntu partition, but it may be beyond repair. I would go ahead and quit testdisk, and then do:
```
[[ $(mount | grep sda1) ]] || sudo e2fsck -fv /dev/sda1
```
Note this time the e2fsck does not use the "p" option; please post the output.

---

### Post by Ederico on 2009-02-22
```
e2fsck 1.41.3 (12-Oct-2008)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  137556 inodes used (5.24%)
    3314 non-contiguous inodes (2.4%)
         # of inodes with ind/dind/tind blocks: 8011/278/16
 1874565 blocks used (17.86%)
       0 bad blocks
       3 large files

  112311 regular files
   14579 directories
      79 character device files
      40 block device files
       8 fifos
     109 links
   10520 symbolic links (9707 fast symbolic links)
      10 sockets
--------
  137656 files
```

---

### Post by caljohnsmith on 2009-02-22
OK, next try:
```
sudo mount /dev/sda1 /mnt && nautilus /mnt &
```
That should pull up a nautilus browser and allow you to browse your files, assuming the sda1 partition mounts OK. Let me know if you can access your personal files or not.

---

### Post by Ederico on 2009-02-22
Didn't work, and the partition can't be seen in order to be mounted now.

---

### Post by caljohnsmith on 2009-02-22
> **Ederico said:**
> Didn't work, and the partition can't be seen in order to be mounted now.
Ederico, please be more specific if you want help; what do you mean the partition can't be seen? Can you post the results of the mount command? Does fdisk still show your sda1 linux partition?

---

### Post by Ederico on 2009-02-22
The partition doesn't show in Places and in Nautilus any longer, usually it would and clicking on it would ask for the password to mount it.

For the last command I got - 

```
[1] 10892
```

---

### Post by caljohnsmith on 2009-02-22
OK, how about posting the output of:
```
ls -l /mnt /mnt/home
```

---

### Post by Ederico on 2009-02-22
```
ubuntu@ubuntu:~/Desktop$ ls -l /mnt /mnt/home
ls: cannot access /mnt/home: No such file or directory
/mnt:
total 4716
-rwxr-xr-x 1 root root 1605637 1907-11-30 17:32 ??.???
-rwxr-xr-x 1 root root 1605636 1907-11-29 17:32 ??.???
-rwxr-xr-x 1 root root 1605638 1907-12-01 17:32 ??.???
-rwxr-xr-x 1 root root       0 1980-01-01 00:00 ??(.??y
-rwxr-xr-x 1 root root       0 1980-01-01 00:00 ??(.??y
-rwxr-xr-x 1 root root       0 1980-01-01 00:00 ??(.??y
-rwxr-xr-x 1 root root       0 1980-01-01 00:00 (?y.*?y
```

That doesn't look good I guess.

---

### Post by caljohnsmith on 2009-02-22
No, unfortunately that doesn't look good at all. You could try running testdisk on the partition again to see if the fsck helped at all, but I don't think it will make any difference. Assuming you still have testdisk 6.10 on your desktop, you could run testdisk using:
```
sudo testdisk-6.10/linux/testdisk_static /dev/sda1
```
Then do "proceed", "none", "Analyze", "quick search", and then do "p" to list the root directory of the partition. You can use your arrow keys to try and navigate through the directories and see if you find anything. If testdisk doesn't find anything, you could use a tool like "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")" to try and recover all the files that it can from the partition. You will need a drive/partition at least as big as sda1 to save all the recovered files to though.

---

### Post by Ederico on 2009-02-22
All I got trying to access my personal directory under the home directory was "No file found. File system seems damaged".

Thanks for the tip about photorec, unfortunately my HDD doesn't have the required space. Perhaps I could try getting some external USB HDD?

---

### Post by caljohnsmith on 2009-02-22
> **Ederico said:**
> 
Thanks for the tip about photorec, unfortunately my HDD doesn't have the required space. Perhaps I could try getting some external USB HDD?
Sure, an external USB drive should work fine, but keep in mind it should ideally be at least 40 GB since that is the size of your sda1 partition. Since you probably don't have 40 GB worth of files in your sda1 partition, you might be able to get by with a lesser-capacity drive, but it would be better if you can just find a 40 GB or larger USB drive.

---

### Post by Ederico on 2009-02-23
Hello again, I used PhotoRec to recover my files saving them in an adequately big partition of my desktop PC's HDD. However, files are not named as they were or would have been, I guess this is normal.

I would like to search through the directories with the recovered files for particular files using extensions such as .mp3, .mp4, .doc, .odt et cetera. How can I possibly do this?

Thanks a lot for the help, if I can manage to search and organise files as stated above it would be great (and I learned a bit in the process as well).

Ederico.

---

### Post by Ederico on 2009-02-23
Ok, I probably managed just using Nautilus!

---

### Post by caljohnsmith on 2009-02-23
I'm glad that photorec at least was able to recover a lot of your files, but as you've all ready expressed concern about, it is a big job to go through them all to find what you are looking for. Also, since photorec often recovers files without any identifying extension, I would recommend using the linux "file" command to identify the files, because "file" actually analyzes the file to figure out what it is, not what the file claims to be just by its extension (or lack thereof). The first thing I would recommend is changing the the ownership of all of the recovered files to yourself, because photorec by default saves everything as root user if I remember correctly. Therefore, I would do:
```
sudo chown [COLOR="Blue"]<username>[/COLOR]:[COLOR="Blue"]<username>[/COLOR] -R /[COLOR="Blue"]photorec_dir_path[/COLOR]/*
```
Just be careful with the chown command, because it will recursively change all files/directories to your user name in the "photo_dir_path" that you give it, so be careful to specify the correct path. Also replace <username> with your user name. Next you could do something like:
```
find /[COLOR="Blue"]photorec_dir_path[/COLOR] -type f -exec file {} \; > ~/Desktop/Recovered_file_types.txt
```
That command will go through all the photorec recovered files and use "file" to identify each one; the output is saved to a "Recovered_file_types.txt" on your Desktop. Of course that will take a long time since it will have a lot of files to process, but you can see its progress by looking at the "Recovered_files_types.txt" file on your desktop. Once it is done, to find all the recovered mp3 files you can do:
```
grep -i mp3 ~/Desktop/Recovered_file_types.txt
```
Let me know how that goes or if you run into problems.

---

### Post by Ederico on 2009-02-23
I'm actually using another method I found online. I checked this page out and I'm sorting all files according to their extension using a modified find command found on this page: [http://builtbackwards.com/projects/photorec-sorter/](http://builtbackwards.com/projects/photorec-sorter/)

The command I'm talking about is found in the first paragraph. I'll go through that process with all the file extensions, should I still follow your directions and if yes, why?

Thanks a lot.

---

### Post by caljohnsmith on 2009-02-23
I didn't actually look at the script code, but if it does what it claims to do, that script is definitely a good place to start. The only limitation is that the script sorts all files by extensions, and as I tried to point out in my previous post, some recovered files will not have extensions and yet might be the file type you are looking for. So once that script is done sorting the files with extensions, I would recommend running the commands from my previous post on the remaining files that don't have an extension, and then you will probably have the maximum chance of recovering all your mp3, mp4, doc, etc. files.

---

### Post by Ederico on 2009-02-23
Thanks, shall do as you said, you've been of tremendous help. :)

---

