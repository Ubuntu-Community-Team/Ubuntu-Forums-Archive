---
title: "quicktime"
date: 2005-10-29
forum: Desktop Environments
---

### Post by veritas366 on 2005-10-29
The mysteries of multimedia in Ubuntu still elude me.  I have totem xine...the about:plugins has it registered to play .mov files, but I get this error:

> Totem could not play 'http://movies.apple.com/movies/weinstein/transamerica/transamerica_h480.mov

there is no plugin to handle this movie.

I've actually gotten one or two to play.

I also have realplayer installed but when I try to play the video off of weather.com it plays the audio only of the commercial, then freezes.

I just upgraded to Breezy, which was of course stupid, because I had these things working in hoary. Oh well, if anyone has any ideas, let me know please.

---

### Post by Xian on 2005-10-29
I always use VLC to play .mov files. I tested your link in that media player and it works fine. You can install it (and the associated plugins) by enabling the universe repos and using Synaptic. I have VLC setup in my Opera web browser as the default program associated with quicktime files so I can stream them directly from the web.

```
$ apt-cache policy vlc
vlc:
  Installed: 0.8.4-svn20050920-3+hal0ubuntu3
  Candidate: 0.8.4-svn20050920-3+hal0ubuntu3
  Version table:
 *** 0.8.4-svn20050920-3+hal0ubuntu3 0
        500 http://us.archive.ubuntu.com breezy/universe Packages
        100 /var/lib/dpkg/status
```

---

### Post by veritas366 on 2005-10-29
Thanks,

Actually, it seems that only SOME of those links don't work.  I think some quicktime vids may have some other programming with them, Like Activex or something.  However, you were able to get that link to work and I couldn't for whatever reason.  

It's also not completely transparent how to associate media players with media types in Firefox.  I actually had a great multimedia extension that worked great. Very easy to associate the right player with media types but it didn't seem to work when I upgraded to Breezy.  

I'll look for some more real media sites other than weather.com to see if I can get THAT player working.

---

### Post by mutenroid on 2005-11-17
[QUOTE=Xian]I always use VLC to play .mov files. I tested your link in that media player and it works fine. You can install it (and the associated plugins) by enabling the universe repos and using Synaptic. I have VLC setup in my Opera web browser as the default program associated with quicktime files so I can stream them directly from the web.
[/QUOTE]

How do you setup vlc in opera for stream quicktime video??

Could you show me, step by step? :rolleyes: 

Sorry for my english and thanks

---

### Post by jctosu on 2007-08-15
install the following packages, you may need to enable the medibuntu repos [(http://medibuntu.sos-sts.com/repository.php]("http://medibuntu.sos-sts.com/repository.php"))

mplayer
mplayer-firefox
win32codecs
libquicktime
gstreamer ffmpeg
gstreamer gl
gstreamer plugin base
gstreamer plugin good
gstreamer plugin bad
gstreamer plugin ugly
gstreamer plugin bad multiverse
gstreamer plugin ugly multiverse


Search for vlc plugin for firefox.

DO NOT INSTALL IT.

If it is already installed, uninstall it.

Mplayer plugin seems to work much better, especially for QT format, and vlc plugin will take priority over mplayer in firefox.

(For someone who wants to manually uninstall vlc plugin, it's in /usr/lib/firefox/plugins)



Now hit Alt+F2 add copy in the following:

Quote:

gksudo gedit /etc/mplayer/codecs.conf

In the menu go to Search-->Find

type in "ffsvq3" and hit ok

comment out the paragraph so it looks like this:

Quote:

#videocodec ffsvq3

# info "FFmpeg Sorenson Video v3 (SVQ3)"

# status working

# fourcc SVQ3

# driver ffmpeg

# dll svq3

# out YV12,I420,IYUV

save the document



and restart firefox!


worked for me on most quicktime files, not all files work for me but a lot of them do

---

