---
title: "ziping files"
date: 2010-04-11
forum: Desktop Environments
---

### Post by Mia1990 on 2010-04-11
ok i am needing to compress or zip a 5.5gb file as small as i can get it how would i do this i know i right click it but what format will give me the best compression or is there a better way to do it?
Thank you

---

### Post by shaka_zulu on 2010-04-11
i think that .tar.gz will give better compression than .zip. I think that i found this information once somewhere on the net but can not confirm that. I am using tar.gz since that is the native one for Linux or at least Ubuntu.

---

### Post by Mia1990 on 2010-04-13
I am trying to compress 5.5gb for backup on a 4.7gb dvd so i can do a clean install of ubuntu 10.04 when it comes out but when i compress it to a tar.gz its still about 5.4gb i have got to be doing something wrong.

---

### Post by kellemes on 2010-04-13
What kind of data are you trying to compress?
If you want to backup the system using tar.. maybe this link helps?
[https://help.ubuntu.com/community/BackupYourSystem/TAR]("https://help.ubuntu.com/community/BackupYourSystem/TAR")

---

### Post by gmargo on 2010-04-13
It depends on what is in that 5.5gb file.  It sounds like you gained nothing by compressing with gzip, so is your file already compressed?  Is it all .mp3 files (which won't compress much)?  Or if it's a system backup, did you back up too much (like executables etc that are easily recovered)?

---

### Post by iponeverything on 2010-04-13
You can see if bzip does any better.

---

### Post by Mia1990 on 2010-04-13
the files are mixed some mp3's and video;s some are.deb's and picture's just different file type's i make a folder put everything i am wanting to compress in it then i right click on the folder and click compress it but it's not making it very much smaller when i select the tar.gz option

---

### Post by mister_p_1998 on 2010-04-14
Does TAR have a split option? you could split your data onto two dvd's
Steve

---

### Post by dominiquec on 2010-04-14
Consider also where you'll be saving the file to.  If you're sending it to a FAT/VFAT-formatted USB drive, be aware of the 4GB file size limit.  You'll need to break it up into smaller chunks.  

For this, you'll need to install p7zip-full or rar.  The Create Archive... dialog that appears when you right click on a file should recognize these formats once they're installed.

---

### Post by Drenriza on 2010-04-14
what command did you use to compress the file?

---

### Post by oldos2er on 2010-04-14
Mp3s are already compressed, and possibly the video files are too, depending on which format they are.

---

