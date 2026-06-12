---
title: "Installation help"
date: 2006-07-21
forum: Desktop Environments
---

### Post by rand0m3r on 2006-07-21
Hi, i currently have my hard drive partitioned for dual-boot. but now i'd like to use the hard drive as a whole (no partitions), install both kubuntu and windows xp and allow both OSes to read off the same drive. i heard that was possible somewhere.

so firstly, can someone tell me how i can merge the partitions back to the single hard drive. and then the installation steps after that. thanks.

---

### Post by mogelhead on 2006-07-22
I advice against it.

When I googled the subject, I found this: [linux-windows-both-same-partition]("http://www.astahost.com/linux-windows-both-same-partition-t12119.html")

It talks about putting Slackware Linux on a Windows 9X FAT16 partition. Not exactly what you wanted but there are a number of arguments against doing it that are worth reading.

May I ask why do you want to do this?

If you want to do this so that you can share files between the two operating systems there are other solutions. (Sorry if you already know this.)
[LIST=1]
[*]One NTFS Windows partition, one Linux partition and one FAT32 partition for sharing files.

[*]One NTFS Windows partition, one Linux partition. Configure Linux to access the windows partition (read only) and use some program in Windows to access the Linux partition ([explore2fs]("http://www.chrysocome.net/explore2fs"))

[*]I have a Linux file server with SAMBA where I store all my music and movies. From my destop computer I can access the files both from Windows XP and Ubuntu Linux.
[/LIST]

---

### Post by rand0m3r on 2006-07-22
i thought it'd be more efficient if they could both read off the same drive. that way, i don't need to put duplicates of files on my computer, especially music.

---

### Post by grim1234 on 2006-07-22
As above, just use one small partition for each os and use the rest of the space for a large fat32 partition. This way you can put all music / files on the fat32 partition and linux will mount on boot, and windows will use automatically. 

This is what I do and it works very well.

So here's an example partition scheme for one disk :

/dev/sda1 : Linux          ext3          <-- linux install
/dev/sda2 : Linux Swap 
/dev/sda3 : Windows        ntfs          <-- windows install
/dev/sda4 : Shared         vfat (fat32)  <-- music etc...

I'd run the ubuntu live cd and format the drive as above (using parted or cfdisk or similar). If you're not using sata drives then it's called /dev/hda instead of /dev/sda.

Then install windows, then linux.

---

