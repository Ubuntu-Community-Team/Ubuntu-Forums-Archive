---
title: "mkisofs unable to create dvd-video image"
date: 2006-01-03
forum: General Help
---

### Post by Moshe on 2006-01-03
Well, the title says it all.  I'm stumped.  I've googled this problem, and I read the man page.  Here's what I have so far:

I have a mini-dv camera and I dual boot.  Foreseeing the possibility that I might want to work with the video from the camera in both Windows and Linux, I installed a second hard drive that was formatted FAT32.  It was onto this drive that Kino sent the dv data which it subsequently transformed into mpeg files for the dvd.

Using QDVDAuthor, I have created my dvd filesystem, with the AUDIO_TS and VIDEO_TS folders.  However, mkisofs will, without fail, return an error when I attempt to write a dvd-video image.

mkisofs: Unable to make a DVD-Video image.

Great.  Very descriptive.  It gives no clues what I did wrong or where I need to look to fix it.  I see nothing in dmesg regarding any iso writing.

I tried moving the files from my FAT32 partition to my home partition which is Reiser in the hopes that perhaps mkisofs was disliking FAT, but that returned nothing as well.

Any suggestions from the group?

---

### Post by limit223 on 2006-01-04
mkisofs -dvd-video -udf -o dvd.iso /directory/

Some info you may find [here]("http://linuxgazette.net/issue83/stoddard.html")

---

### Post by Moshe on 2006-01-05
The problem lies with mkisofs.  For some reason, mkisofs refuses to create the dvd image.  I appreciate you trying, but that link has nothing that explains my problem.

---

### Post by kverde on 2006-02-02
According to the mkisofs man file, the filenames MUST be in uppercase.  Possibly the reason?

---

### Post by volcanomike on 2007-02-11
..

---

### Post by motumboe on 2007-03-07
> **kverde said:**
> According to the mkisofs man file, the filenames MUST be in uppercase.  Possibly the reason?

I've just had the same problem and I've found out that you're correct. I've created the necessary files with dvdauthor, but I was on a FAT32 partition and the created files were not all-caps.

Thanks :-)))

---

### Post by helpdeskdan on 2007-03-20
Same exact problem, I'll see if I can get it off my fat32

---

### Post by distantradio on 2007-04-15
This is caused by the default "shortname=lower" mount option for fat32 file systems: dvdauthor creates upper case filenames like AUDIO_TS, but they come out as lower case; this makes mkisofs fail because it expects upper case filenames when run with -dvd-video.

To fix this, mount the file system with some other shortname option by adding it to the mount options of the drive in /etc/fstab. See "man mount" for the possible options, shortname=winnt worked for me, I guess all except shortname=lower will solve this problem.

Here is the line in my fstab:
/dev/sda8      /media/fat vfat   rw,utf8,users,umask=000,shortname=winnt 0 1

---

