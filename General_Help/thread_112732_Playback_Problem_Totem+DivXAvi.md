---
title: "Playback Problem: Totem+DivX/Avi"
date: 2006-01-04
forum: General Help
---

### Post by comshock25 on 2006-01-04
I installed a fresh 5.10. All went fine. But when I played videos on totem, the sound is not in sync with the video :( I have installed ubuntu many times on my system but never got this problem before. Please help.

---

### Post by bored2k on 2006-01-05
Install the needed codecs with [http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix)

---

### Post by professor_chaos on 2006-01-05
if that doesnt work take a look here
[http://www.ubuntuforums.org/showthread.php?t=70523&highlight=audio+sync](http://www.ubuntuforums.org/showthread.php?t=70523&highlight=audio+sync)

---

### Post by StefanoCole on 2006-01-05
Well, I had the same problem, also after installing the codecs, Totem still played videos out of sync with audio. That didn't happened with Warty and Hoary. Then I installed Xine-ui and that solved my problem (i.e. with Xine-ui videos are in sync with audio).

Stefano

---

### Post by cacharreo on 2006-01-05
all you need to do is from console type:

*$sudo aptitude install libdivx4linux* (this is for divx)

*$sudo aptitude install ffmpeg* (this one for mpg)

You also should try for most of video and audio formats:

[I]$sudo aptitude install gstreamer0.8-plugins
$ sudo aptitude install gstreamer0.8-lame
$ sudo aptitude install gstreamer0.8-ffmpeg
$ sudo aptitude install w32codecs
$ sudo aptitude install lame
$ sudo aptitude install sox
$ sudo aptitude install mjpegtools
$ sudo aptitude install vorbis-tools
$ gst-register-0.8[/I]

 Ubuntu is esay and great

---

### Post by Perfect Storm on 2006-01-05
[QUOTE=cacharreo]all you need to do is from console type:

*$sudo aptitude install libdivx4linux* (this is for divx)

*$sudo aptitude install ffmpeg* (this one for mpg)

You also should try for most of video and audio formats:

[I]$sudo aptitude install gstreamer0.8-plugins
$ sudo aptitude install gstreamer0.8-lame
$ sudo aptitude install gstreamer0.8-ffmpeg
$ sudo aptitude install w32codecs
$ sudo aptitude install lame
$ sudo aptitude install sox
$ sudo aptitude install mjpegtools
$ sudo aptitude install vorbis-tools
$ gst-register-0.8[/I]

 Ubuntu is esay and great[/QUOTE]



Without the "**$**" ;)

---

