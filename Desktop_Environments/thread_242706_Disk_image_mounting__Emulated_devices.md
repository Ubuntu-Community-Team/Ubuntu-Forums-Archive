---
title: "Disk image mounting / Emulated devices"
date: 2006-08-24
forum: Desktop Environments
---

### Post by pinesolpirate on 2006-08-24
I have several dvd images on my computer, and I'd like to be able to mount and view them.  The windows equivalent to what I want to do is mounting with daemon tools then opening WMP and watching the movie.

I can and have mounted the images just fine, for example:
```
sudo mount -t iso9660 -o loop /media/hdb1/Sorted/movie.iso /media/movie
```

The problem is, this isn't an emulated device like a SCSI passthrough on windows.  So all you get is the disc filesystem, and none of the players I've installed have done well here.

I can watch single .vobs with mplayer and totem, but getting it to just "pretend" the whole thing is a dvd doesn't work.

VLC looked hopefull, but I never figured out the right combination to get it going.

Xine just errored out.

Anyway, this isn't a huge deal, but if anyone has experience tricking a media player into running this sort of thing, I'd appreciate the help.

-John
(First post, yay.)

---

### Post by johnsd8 on 2006-08-24
xine should work fine.

xine 'dvd://path/movie.iso'

mplayer as well I believe.

---

### Post by Belyel on 2006-08-31
> **pinesolpirate said:**
> I have several dvd images on my computer, and I'd like to be able to mount and view them.  The windows equivalent to what I want to do is mounting with daemon tools then opening WMP and watching the movie.

I can and have mounted the images just fine, for example:
```
sudo mount -t iso9660 -o loop /media/hdb1/Sorted/movie.iso /media/movie
```

The problem is, this isn't an emulated device like a SCSI passthrough on windows.  So all you get is the disc filesystem, and none of the players I've installed have done well here.

I can watch single .vobs with mplayer and totem, but getting it to just "pretend" the whole thing is a dvd doesn't work.

VLC looked hopefull, but I never figured out the right combination to get it going.

Xine just errored out.

Anyway, this isn't a huge deal, but if anyone has experience tricking a media player into running this sort of thing, I'd appreciate the help.

-John
(First post, yay.)

One other thing that I've found works in Ubuntu is after you've mounted the image, or if you just copy the folders from a dvd, you can drag the entire containing folder into Totem and it will read it like a DVD.  For example, if the iso mounts into /mount/iso1, you should see subfolders video_ts and audio_ts, although sometimes discs don't have audio_ts.  Just drag the folder iso1 into Totem and it will play the disc as a DVD.

---

### Post by rpalyvoda on 2006-12-17
> **Belyel said:**
> One other thing that I've found works in Ubuntu is ...if you just copy the folders from a dvd, you can drag the entire containing folder into Totem and it will read it like a DVD. ..

WOWWWWWW!!!!!!!!!!!!!!!!!!!!

Great!!! I'd never even dreamed of anything like that!!!!!

thanks a lot!!!

---

