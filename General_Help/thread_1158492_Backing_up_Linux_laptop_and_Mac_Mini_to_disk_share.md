---
title: "Backing up Linux laptop and Mac Mini to disk shared with Mac"
date: 2009-05-13
forum: General Help
---

### Post by calibre97 on 2009-05-13
I have a Dell D630 laptop with a 250GB drive on which I have installed the following:
/dev/sda1   XP  (primary partition)
(everything else on an extended partition)
/dev/sda5   Data1 (formatted ext3)
/dev/sda6   Data2 (formatted ext3)
/dev/sda7   Linux Mint 6 /home (ext3)
/dev/sda8   Linux Mint 6 /     (ext3)
/dev/sda9   swap
/dev/sda10  Linux Mint 7 /home (ext3)
/dev/sda11  Linux Mint 7 /     (ext3)
/dev/sda12  Kubuntu 9.04 /home (ext4)
/dev/sda13  Kubuntu 9.04 /     (ext4)

I also have a Mac Mini with a 120GB internal drive.

I've been backing up the Mini to its own 120GB 2.5" drive using SuperDuper. 
I've been backing up the Dell D630 also to its own 120GB 2.5" drive (the 2 Data partitions on the internal drive aren't really full right now so all the partitions fit on the 120GB drive). I boot to an Acronis 11 CD to backup the XP partition, and I boot to a RescueCD and use rsync to backup the Linux partitions. 

I now have a nice, new 1TB 3.5" external drive I'd like to use for backing everything up. I would connect the drive to the Mini via Firewire 800 for that backup, and would connect the drive to the Dell via USB to back it up.

My question is how to set up the 1TB to serve all 3 platforms. I'd ideally like an NTFS partition for XP, HFS+ for Mac OS X, and ext3 and ext4 partitions for the Linux stuff. I'd leave a big chunk of the drive HFS+ for ripping movies, etc, and accessible from the Mini. I really only need space and the other filesystems for backing up.

Should I even care about maintaining the file systems on the partitions, or just TAR up the various Linux stuff? For that, though, won't I still need large file support (meaning can't use FAT32 for universal access)?

Any suggestions on tools/order/layout of the big drive to handle all of this? For example, I could boot up the Dell with a RescueCD and attach the drive via USB to use gparted to create partitions. Any help/advice would be greatly appreciated.

NOTE: To head off some expected advice: I already have the drive and enclosure, which I'd like to keep local to use it connected to the Mini (scratch space for iMovie/iDVD, storing ripped DVDs as backup and so on). No, I won't 'just go out and buy a home NAS' or similar. Also, I don't see bothering to set up SSH on the Mini because frankly it'd be easier and faster to just connect the drive with the laptop over USB. My main concern in this project is with how to partition the drive into many slices using multiple file systems.

---

