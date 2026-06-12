---
title: "Windows-Ubuntu Interface?"
date: 2006-02-05
forum: Desktop Environments
---

### Post by tension on 2006-02-05
I need to access Windows XP from my Ubuntu desktop (or vis versa)
  I'm running both systems on the same box but different drives.  The LInux drive is formatted by Windows and Ubauntu to FAT32.  The XP drive is of course, NTFS.

  Any suggestions on applications?  Other thoughts?
 
  (I was considering using WINe, but see its compatible with WIN31 to 98 systems only.)

e

---

### Post by jhbumby on 2006-02-05
Why don't you just dual boot?  Partition your hardrive and go from there?

---

### Post by jhbumby on 2006-02-05
Go to this website, they're a couple of dorks, but aren't we all.  Plus they got it down.

[http://video.google.com/videoplay?docid=-6104490811311898236&q=](http://video.google.com/videoplay?docid=-6104490811311898236&q=)

---

### Post by RAOF on 2006-02-05
[QUOTE=tension]I need to access Windows XP from my Ubuntu desktop (or vis versa)
  I'm running both systems on the same box but different drives.  The LInux drive is formatted by Windows and Ubauntu to FAT32.  The XP drive is of course, NTFS.

  Any suggestions on applications?  Other thoughts?
 
  (I was considering using WINe, but see its compatible with WIN31 to 98 systems only.)

e[/QUOTE]
When you say "access", what exactly do you mean?  Do you mean "access Windows' files from Ubuntu"?  The "Accessing Windows Drives" link in my sig should help you there.  Although since the Windows drive is NTFS you won't be able to write to it at all from Ubuntu.  That's just the way things are :(

If you want to run Windows programs under Ubuntu, don't bother - you've got a Windows install which will do the job much better :)

I really doubt that your linux drive is formatted FAT32 - if it was, you would be able to see it & read/write to it in Windows just fine.  Also, last time I checked, linux would not run from a FAT32 drive - it lacks basic features like file permissions which make it unsuitable for a linux install.  Ubuntu probably formatted it EXT3 - you might want to check out [www.fs-driver.org](www.fs-driver.org) - they have Windows drivers for the EXT2/3 file system so you can access that drive in Windows.

---

### Post by tension on 2006-02-05
*jhbumpy*
  Yes I recognize many of the screens in the video from my installs (although I didn't have banjo music playing when I did it, its a nice touch for microsoft), but I already have a dual boot through GRUB .  The problem is I don't think you can boot both OS's at the same time. I put Ubuntu on the second drive because (a) I thought that was the safest way to dual boot and (b) I had the extra drive (13G) and thought I might put it to good use.

*RAOF*
  Yes, you could be right about the formatting.  What started out as FAT32 may indeed be something else I never heard of before today.  
  No, I don't expect to run Window based programs on Ubuntu.  Transfering of files would be enough for now.  
  I like many people would like to move up to a better system full-time, but can't make the break: apllication vendors (among other reasons), don't go where's there's no profit.  So I'll make do with schizophrenic computing.
  Anyway I'll give the links a try as they look to be what I'm looking for.


Thanks all for your replies,

e

---

