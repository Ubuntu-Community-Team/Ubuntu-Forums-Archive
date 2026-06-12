---
title: "Rythm Box will not play streams"
date: 2006-02-21
forum: Desktop Environments
---

### Post by richardstrausbourg on 2006-02-21
My Rythm Box (and Totem) will not play streams.
Like:
 	  Launch MP3 Stream (.pls)
    [iTunes, QuickTime, Real Audio, WinAmp]
		
	Launch MP3 Stream (.m3u)
    [Windows Media, Real Audio]

Totem says we need a decoder.

Where? What? How? to fix?

Richard Strausbourg

---

### Post by Perfect Storm on 2006-02-21
enable universe in the sourcelist. Also add multiverse and PLF.

```
sudo gedit /etc/apt/sources.list
```

Uncomment the lines where there's a #

add:

[b]## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]

```
sudo apt-get update
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg w32codecs lame sox ffmpeg mjpegtools vorbis-tools libdvdcss2 gstreamer0.8-plugins-multiverse avifile-divx-plugin avifile-mad-plugin avifile-mjpeg-plugin avifile-vorbis-plugin avifile-win32-plugin avifile-xvid-plugin libdvdnav4 libdvdplay0 libdvdread3
gst-register-0.8

```

But you might try mplayer or vlc as they are better to the job.

---

### Post by richardstrausbourg on 2006-02-22
Thanks for the tip! I'm new to Ubuntu and there are so many packages to learn. AND FREE packages at that...

Richard

---

