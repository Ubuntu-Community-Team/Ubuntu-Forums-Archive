---
title: "no preview for videos in nautilus"
date: 2007-06-06
forum: Desktop Environments
---

### Post by ashrack on 2007-06-06
Latelly  I have no more previews available for videos when in icon mode in nautilus.

In Nautilus when I am in ICON mode the video files are not previewed and also when I hover the mouse over an MP3 it doesn't play music.

I tried both TOTEM-XINE, TOTEM-GSTREAMER since from what I have read U need TOTEM to be able to preview video files in Nautilus. I have xinelibs, gstreamer 0.10(all codecs), ffmpeg, mpg123, mpg321 installed

The movies are between 100 and 700mbs in size so that shouldn't be a problem. And also I can play all of the video in TOTEM so it isn't a codec issue.

What else can I do?

I attach a NAUTILUS config screeni:
[ATTACH]34512[/ATTACH]


I've opened a bug report on LP since other ppl also suffer from this. So all of those who have this problem please add your name to the bug report:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/119081](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/119081)

---

### Post by Nonno Bassotto on 2007-06-06
I guess it IS a codec issue, because you use totem-xine to play the videos, but I think totem uses gstreamer to create the thumbnails. I'm not completely sure, though.

---

### Post by ashrack on 2007-06-06
forgot to write that I also tried TOTEM-gstreamer but the video preview still didn&#263;t function

---

### Post by 3006828 on 2007-06-06
how large are the files.. i think nautils defaults wont preview anything over a certin size.

---

### Post by FuturePilot on 2007-06-06
Is this on all videos? I have a few videos that will not show a preview. Most of them do, but a few don't.

---

### Post by ashrack on 2007-06-07
> **3006828 said:**
> how large are the files.. i think nautilus defaults wont preview anything over a certin size.
they are around 700MB

> **FuturePilot said:**
> Is this on all videos? I have a few videos that will not show a preview. Most of them do, but a few don't.
In the OP I mentioned that NAUTILUS **used to **preview all the files. So the only previewable files are now the ones that had already been previewed when this function of NAUTILUS was still working. New video files never get previewed.

---

### Post by Nossie on 2007-06-07
I also have the same problem sadly :(

---

### Post by Myrgen on 2007-08-31
Same here since last updates. Does anyone have a fix for this?

---

### Post by Libi on 2007-09-21
Yes, I have the same problem. I use debian etch and nautilus shows perfectly all the thumbs. In the same directories, ubuntu fails the video thumbs. Pictures are ok. I think the problem must reside in an application helper used by nautilus, that can't use the codecs, also if they are available. This needs further investigation.

---

### Post by Wolki on 2007-09-21
Can someone affected by this please do the following:

Alt-F2, gconf-editor
Navigate desktop -> GNOME -> thumbnailers -> video@x-avi (or the mime type you have problems with instead of avi)
then post the contents of the "command" and "enable" keys

---

### Post by Myrgen on 2007-09-22
Hello,

The problem was solved, for me.
Being a fan of MPlayer, I had uninstalled Totem. Everything was going fine and I could watch video to my content. -Then- came the last update and if I still could watch video, the thumbnails had disappeared.
After the many things I tried unsuccessfully, I reinstalled Totem. I still do not use it, but the thumbnails are back.

Hope this helps.

---

### Post by mysticmatrix on 2007-09-22
> **Libi said:**
> Yes, I have the same problem. I use debian etch and nautilus shows perfectly all the thumbs. In the same directories, ubuntu fails the video thumbs. Pictures are ok. I think the problem must reside in an application helper used by nautilus, that can't use the codecs, also if they are available. This needs further investigation.

Well Totem has been a headache to me in building thumbnails. Every now and then it would not thumbnail .rmvb and other unsupported file. I found mplayer more capable to thumbnail my videos.
See a howto here [http://ubuntuforums.org/showthread.php?t=536209](http://ubuntuforums.org/showthread.php?t=536209)

---

### Post by mysticmatrix on 2007-09-22
> **Myrgen said:**
> Hello,

The problem was solved, for me.
Being a fan of MPlayer, I had uninstalled Totem. Everything was going fine and I could watch video to my content. -Then- came the last update and if I still could watch video, the thumbnails had disappeared.
After the many things I tried unsuccessfully, I reinstalled Totem. I still do not use it, but the thumbnails are back.

Hope this helps.

If you are a mplayer fan, use it for your thumbnails. :) See my previous post.

---

### Post by aroch1 on 2007-11-26
Exactly what I was looking for!

Thanks a lot!

---

