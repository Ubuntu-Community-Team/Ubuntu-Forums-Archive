---
title: "Crash while coping files"
date: 2006-05-17
forum: Desktop Environments
---

### Post by CrazyNetwork on 2006-05-17
When ever I need to move large ammounts of file(s), I prepare myself to reboot countless times. Today I wanted to change the format (ntfs => ext3) of my storage drive (120gb). I used windows and ext2fs to move the data off of the drive and onto my linux drives. I am now trying to move the data back in Kubuntu (Konqueror). I have to copy (Yes, copy, so I don't lose data when it crashes) each archive file one by one. I spend about five minutes copying files and boom! Everything is locked up. A few moments later it has automatically done a hard reboot. I spend the next ten minutes waiting while Kubuntu complains about, and checks, the uncleanly unmounted drives (/ 10gb and /home 70gb). 

To avoid some of these problems I thought I might burn a bunch of the backup archives to a DVD. But to my suprise, it crashed while burning!!! There goes that DVD-R! I do not know where the problem is, but I seem to find it every time I move large ammounts of data. How can this be resolved? 

Some examples...

----------
From:
(hdc2 - ext2) /home - 70mb
To:
(hdb1 - ext3) /media/hdb1 - 120gb

Files:
work_images.zip - 712mb - Copy OK
work_audio.zip - 667mb - Copy OK
work_files.zip - 954mb - CRASH @ 97%

----------
From:
(hdb1 - ntfs) /media/hdb1 - 120gb
To:
HP Invent DVD-R  8x (via K3b)

Files:
mdk_install.iso - 3.6gb - CRASH @ 47%

---

### Post by GeneralZod on 2006-05-17
Something's very wrong there, and the fact that your entire system locks up makes me think it's something to do with your hardware.  However, the fact that Windows doesn't crash belies  this.

Do you know your way around the command-line? If so, try copying your files using the "cp" command.

---

### Post by CrazyNetwork on 2006-05-17
I am ahead of you there, good tip though. I seem to be able to copy the files through Konsole with the "cp" command. But that still leaves me with the inability to burn DVDs.

---

### Post by CrazyNetwork on 2006-05-17
Holy smokes!!! The "cp" command seems to be copying the files with great speed. I don't know the transfer rate but it just copied 700.6mb in about ten seconds. Konqueror (when not crashing) would take about 45 seconds.

---

### Post by regeya on 2006-05-24
[QUOTE=CrazyNetwork]
To avoid some of these problems I thought I might burn a bunch of the backup archives to a DVD. But to my suprise, it crashed while burning!!! There goes that DVD-R! I do not know where the problem is, but I seem to find it every time I move large ammounts of data. How can this be resolved? 
[/QUOTE]

Similar problem here, maybe -- copying files from data DVDs seems to cause unrecoverable I/O errors, but I can dd the whole dang thing to HD, loopback mount the .iso, and copy the files that way.  At least no freezes.

---

### Post by revenazb on 2006-05-24
I have the exact same problem,

While attempting to copy large files from an external drive the whole system freezes, works fine from the command line however.

I am also unable to unzip large files (1.7 Gigs) the whole system crashes as well.

---

### Post by grubber on 2007-07-30
same problem here
when copying files from external HD the whole system crashes. 

with the commandline  the system freezes but it continues on copying, after that the system is useless so a reboot is needed.
with livecds from older ubuntu versions this gives no problem

also i have the impression that this happens when downloading big files...

is this currently getting investigated? 

greetz

---

