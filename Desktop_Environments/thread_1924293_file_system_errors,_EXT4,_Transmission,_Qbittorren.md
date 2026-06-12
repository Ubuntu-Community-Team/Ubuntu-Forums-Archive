---
title: "file system errors, EXT4, Transmission, Qbittorrent, K3B"
date: 2012-02-12
forum: Desktop Environments
---

### Post by gbrowning on 2012-02-12
Have a problem with the file system developing errors and becoming inaccessible.  This is the Home Folder drive and the entire system slows to unusable. This does not appear to be a hardware problem. FSCK restores the system to functionality but the system will slow to a stop again as the home folder is accessed. It seems to be associated with larger files and manipulating larger files.  Transmission, K3B, and/or Qbittorrent are involved somehow.  I am using a GUID and EXT4 file system on a machine with 3 hard drives.

Ubuntu 11.10 on a 32GB SSD 
Home Folder on a 633GB partition on a 750GB Hard drive
Extraneous storage on a 750 GB drive partitioned into two halves.

This problem first appeared when the Home folder was on the same drive as the system. The drive appeared as full though there was room.  This happened during a session when Transmission was downloading a 5.1GB file

The problem seemed to be solved by moving the home folder to a plenty large enough, newly partitioned drive.

This problem re-appeared while qbittorrent and K3B were running concurrently.  The machine was left to run and when I returned a day later any process using the home folder drive had stopped and returned the message "drive full" or "file system Read Only" or combinations thereof.

Disk Utility shows the disk as healthy.  I believe this.
Disk Utility showed the filesystem as unclean
I booted a Debian live disk (mounts quicker than Ubuntu...sorry!) and ran FSCK which found and repaired seven or eight orphaned inodes.

Booting back into Ubuntu the system works perfectly at first then begins to bog as it accesses the home folder. Even lightweight processes slow to a stop as the system Thrashes with the home folder drive.

I did find that K3B was using the small 30GB system drive for it's temporary files.  The file it was building was 25GB all by itself but I do not know how large the tmp files get or if K3B pays attention to drive space.

I need some suggestions on how to repair the system then prevent this from happening again.

ADDITIONAL INFORMATION  EDIT:
   
    Torrents are broken into thousands of bits.  It seems that the pieces were not being spiced together correctly or that the handles were being lost.  The Temporary files created for the Transcoding are also many pieces.  The temp files for transcoding and the incomplete torrent files have now been purged and the system is working properly for the moment.  Configuration files for Opera and for Thunderbird went missing so perhaps others are missing as well.
    Are there any ideas as to the cause of this?  Faulty Memory?  it tests out as good.  Bad Hard drives?  They test good as well, one is showing signs of premature failure but it was not involved in these processes.

---

### Post by Bobhuber on 2012-02-12
You need to put your tmp and log files on the large drive with sym links to them. That should prevent filling the SSD drive and also help with the write cycles on the drive. In fact ANY folder that you do a lot of writing to should be external to the SSD with links.

---

### Post by gbrowning on 2012-02-12
Thank you for that tip Bobhuber.  I will take that step as a preventive measure both for read/write cycles and for accidental over filling.

---

