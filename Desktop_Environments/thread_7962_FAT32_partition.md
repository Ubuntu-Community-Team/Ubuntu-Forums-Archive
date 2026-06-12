---
title: "FAT32 partition"
date: 2004-12-13
forum: Desktop Environments
---

### Post by johnp on 2004-12-13
Hi!

I got a problem with a mounted FAT32 partition where files and folders aren't visible and the partition sometimes disappear from Windows. 

What I intend to do is set up a shared partition area for my Windows and Ubuntu installation where files are to readable and writable from both OS'. The partitions are:

/dev/hda1 - Windows
/dev/hda2 - supposed to be FAT32 shared partition
/dev/hda3 - Ubuntu swap
/dev/hda4 - Ubuntu Linux

I've used this kind of shared setup earlier when I was running the original Debian distro but that was on a HP NX7010, this is on a Dell D600. Another difference with the current installation to the earlier version is the order of the partitions. Previously the shared area came last among the partitions, ie /dev/hda4. I'm not sure if that has something to do about it.

I've been running this setup earlier without a fuzz, but now I just can't get to work. This is the setting that I've used, with a group called winuser, which I'm member of.

/dev/hda2      /mnt/exchange   vfat    users,rw,exec,gid=winusers,umask=000

When using these mount options all files copied from Ubuntu aren't visible from Windows. I can actually write files to the shared area, no permission problems or write failures are reported.  If I create a text file in Windows and write to the file from Ubuntu, then the changes can be seen from Ubuntu but the file seems untouched when viewing it from Windows.

I read in the forum about another user having some trouble with FAT32 partitions and he was recommended using this line in fstab:

/dev/hda2       /mnt/exchange   vfat    users,uid=1000,auto     0       0

The result is that the partition disappears from windows, ie D:\ disappears.

Anyone got a clue?

By the way thanks for Ubuntu
// John

---

### Post by TravisNewman on 2004-12-13
This is not the appropriate section. Questions and requests for assistance should be in the appropriate support section at the top. This section is for FAQs and HOWTO's that people have made. 

Can someone with power here move this?

---

### Post by adbak on 2004-12-13
I found that by adding files from Windows (more specifically folders) that they appeared to be a single file, which didn't let me explore the many folders and sub-folders full of files (mp3s).  But when I added these files using Linux, everything was fine.  I know, this doesn't help you at all, but perhaps this could help a future visitor get a better glimpse of this problem or inconsistency.

---

### Post by johnp on 2004-12-14
Something similar happened to me when I in desperation tried different setups in /etc/fstab. I believe it appeared when changing or removing the gid or uid. Directories turned to files and when selecting any of the files they just disappeared.

// John

---

### Post by johnp on 2004-12-16
I solved the problem with a radical solution, reinstallation of Ubuntu. This time I partitioned the disk as follows:

/dev/hda1 - Windows
/dev/hda2 - Swap
/dev/hda3 - Ubuntu Linux
/dev/hda4 - Fat32

When reinstalling Ubuntu I removed all partitions but the one containing Windows. Then I created the partitions containing swap and Ubuntu. I left the remaining space as free space, unpartitioned. After the installation I created the fat32 partition from Windows. Now everything worked as expected and I can easily read/write files to the Fat32 space from both OS'.

// John

---

### Post by fisheromen1031 on 2004-12-23
> When reinstalling Ubuntu I removed all partitions but the one containing Windows. Then I created the partitions containing swap and Ubuntu. I left the remaining space as free space, unpartitioned. After the installation I created the fat32 partition from Windows. Now everything worked as expected and I can easily read/write files to the Fat32 space from both OS'.

how did you do this from Windows? I could see in the partition stage during the Ubuntu install, but it sounds like you said that didn't work. 

I'm a newb and don't have any fancy Windows partitioning software.

---

