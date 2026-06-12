---
title: "problem in burning into &quot;not empty&quot; DVD"
date: 2005-12-27
forum: General Help
---

### Post by yccheok on 2005-12-27
Hello,

I have a 4.7GB DVD, which I previously use GnomeBaker to burn 3 files total 1.2 GB into it. Since there are a lot of free space, The DVD is not finalized yet. I decide to add in more file.

I try to login as normal user and use joliet and Rock Ridge options to burn. However, I get the following error message: 

WARNING: /dev/hdc already carries isofs!
About to execute 'mkisofs -V GnomeBaker data cd -p yccheok -iso-level 3 -l -R -hide-rr-moved -J -joliet-long -gui -graft-points 2.AVI=/home/yccheok/Downloads/2.AVI | builtin_dd of=/dev/hdc obs=32k seek=0'
umount: /media/cdrecorder is not in the fstab (and you are not root)
:-( /dev/hdc: unable to proceed with recording: unable to unmount

opps! Then, I try to use sudo to launch gnomebaker as root user. Again, I get the following error message:

WARNING: /dev/hdc already carries isofs!
About to execute 'mkisofs -V GnomeBaker data cd -p root -iso-level 3 -l -R -hide-rr-moved -J -joliet-long -gui -graft-points 2.AVI=/home/yccheok/Downloads/2.AVI | builtin_dd of=/dev/hdc obs=32k seek=0'
INFO: UTF-8 character encoding detected by locale settings.
Assuming UTF-8 encoded filenames on source filesystem,
use -input-charset to override.
/dev/hdc: engaging DVD-R DAO upon user request...
/dev/hdc: reserving 495584 blocks
:-[ RESERVE TRACK failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
/dev/hdc: "Current Write Speed" is 4.1x1385KBps.
:-[ WRITE@LBA=0h failed with SK=2h/ASC=30h/ACQ=05h]:

Please advice. I am using Gnome gnomebaker 0.4.2 and Cdrecord-Clone 2.01a38. Thank you very much

I saw some thread about multisession burining at [http://ubuntuforums.org/showthread.php?t=93020&highlight=gnomebaker](http://ubuntuforums.org/showthread.php?t=93020&highlight=gnomebaker)

However, I am not sure whether my case is belongs to multisession burning... :P

---

