---
title: "xine-check:Your X server doesn't support YV12 overlays."
date: 2006-01-17
forum: General Help
---

### Post by mattbarlow on 2006-01-17
I have problems with dvd and video files playback 
I have tha dma support enabled and i run xine-check it gives a message
         
         Your X server doesn't support YV12 overlays.
         That means xine will have to to color space transformation and scaling
         in software, which is quite CPU intensive. Maybe upgrading your
         X server will help here.
         If you have an ATI card, you'll find accelerated X servers on
         [http://www.linuxvideo.org/gatos/](http://www.linuxvideo.org/gatos/)
         press <enter> to continue...

I do have an ati (radeon 9700 on acer laptop)
and that seems to be an idea for solving the problem (the accelerated x servers) but the link does not work what should i do ?
What is YV12 overlays support? Has anyone had the same problem? how do i install accelerated x server for my ati card? 
thanks a lot...

---

### Post by promet on 2007-01-28
Hey,

Yeah, I had an identical problem, trying to play The life Aquatic DVD. I also got this response from xine-check. I also found that URL to be "bad". I am intrigued by the report that my new Ubuntu Edgy X server is somehow not accelerated!

Anyway, after doing a Google/Ubuntu forum search, I couldn't find any real solution, but did find a workaround.

First I made sure that I had "[libdvdcss]("http://ftp.debian-unofficial.org/debian/pool/main/libd/libdvdcss/")"  for my system the i386 version was the proper one. Whether this was a crucial step I do not know, but I read it as a requirement in another post and though that it could not hurt (it's supposed to resolve some DVD conflict issues).

I used VLC, from the launched app and had all sorts of problems, but - through pure trial and error - I found that running VLC from the command line and directing it to my mounted DVD drive (on my machine this was /media/cdrom-1 - you can navigate to the "/media" directory with Nautilus or from the command line and check the directories for their contents to see which "/media" directory corresponds to your device, i.e. it should have "AUDIO_TS" and "VIDEO_TS" or some such folders for a DVD ) and the DVD, complete with menu navigation, etc., came up and ran pretty respectably:

```
vlc /media/cdrom-1/
```

How and why this worked exactly, I cannot say; but hey, it worked. Also there don't seem to be an excess of good, detailed descriptions on this issue, so...what the hey?

Give it a try for what it's worth.

Also, I have to continue to try to understand the details behind the "Accelerated X server" issue, because I have a decent video card and would like to figure out how to max out its potential with Ubuntu; but that, for the time being anyway, is another issue, as I was able to watch the DVD with my jury-rigged solution. 

Hopefully this wordy diatribe will serve you somehow, good luck!

---

### Post by manni on 2007-02-11
I had the same problem with my ATI Radeon 9250. The following 2 steps solved it:
1. I changed

Section "Device"
Driver "fglrx"

to

Section "Device"
Driver "radeon"

2. I removed the FireGLX driver from my system:
apt-get remove --purge xorg-driver-fglrx

---

