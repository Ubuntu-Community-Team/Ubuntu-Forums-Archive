---
title: "Help playing DVD and mounting data DVD"
date: 2005-08-14
forum: Desktop Environments
---

### Post by tuxfan99 on 2005-08-14
I have a dvd-r that has some actual dvd video on it and some other audio files (so it is a data dvd and a video dvd). If I put it in a real dvd player, the video plays. If I put it in a windows computer, I can open it and browse the contents.
In ubuntu I cannot do either of these things. Both xine and mplayer just say that they cannot access the device. DVD::rip tells me that it cannot find the VIDEO_TS (when I put it in the windows box, I can see video_ts, so it is there).

I also cannot mount it as a data dvd. In windows if I click on properties it says that the format is udf, but if I try to do mount it, it won't work.
```
sudo mount -t udf /dev/hdc /media/cdrom
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I can play normal DVDs fine.

---

