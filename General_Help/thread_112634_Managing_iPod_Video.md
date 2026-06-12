---
title: "Managing iPod Video"
date: 2006-01-04
forum: General Help
---

### Post by sbaush on 2006-01-04
Hi all!
I have a new Apple iPod video 30GB.
I used with success gtkpod and yamipod for managing the music in my iPod, but i have not found any software for managing (import & export) **photos and videos** form/to iPod. 
Does it exists?

Between gtkpod and yamipod what is the better software for managing music in ipod? 

Thanks to all!!!

Bye.

Marco.

---

### Post by sbaush on 2006-01-05
No ideas for video in iPod with Linux??? I don't want to reboot my pc and choose WinXP!!!

---

### Post by frodon on 2006-01-05
No video support for the ipod video with linux for the moment and in addition you will have to re-encode your videos before putting them on your ipod .... thanks apple ! :(

---

### Post by Suzan on 2006-01-05
frodon's right. No video and photo support for linux at the moment. :-( Hope that will be a solution soon.

And gtkpod or yamipod... I like both very much. I personally prefer gtkpod a little more, because with the new version (0.99.2) you can transfer albumcovers to your iPod!

---

### Post by Suger on 2006-01-05
I think the development version of gtkpod supports videos (but I don't have any to upload for the moment, so I haven't tried to compile it).

---

### Post by kaffelars on 2006-01-05
I have successfully compiled and installed the latest gtkpod (0.99.2) on Breezy. It runs, but I haven't gotten around to try the video part yet. And as with all other Ipod-software, it seems that the 5G Ipod cannot be cleanly unmounted. But give it a try :)

---

### Post by endersshadow on 2006-01-05
The latest gtkpod does support videos.  You need to encode your videos to m4v format, at 320x240 resolution.  I'm still working on beating ffmpeg into submission for this, but once I figure this out, I'll post a howto.

As for unmounting:

```
fdisk -l
```

This will give you 2 HDDs from the iPod...should be sd*1 and sd*2 where * is any letter (mine varies).  Assuming *=a, you can just do this:

```
sudo eject -sv sda1
```

Voila, you've ejected.

If you don't have anything else mounted, you can just go straight at it with:

```
sudo eject -sv sd?1
```

:-D

---

### Post by sbaush on 2006-01-06
Can anyone post an howto convert divx in iPod good vieos?

---

### Post by endersshadow on 2006-01-11
[QUOTE=sbaush]Can anyone post an howto convert divx in iPod good vieos?[/QUOTE]
[http://ubuntuforums.org/showthread.php?t=114946](http://ubuntuforums.org/showthread.php?t=114946)

'Tis Done :-D

---

### Post by T*&amp;1p87)v# on 2006-03-30
Hey for photos try
[http://gpixpod.sourceforge.net](http://gpixpod.sourceforge.net)

---

