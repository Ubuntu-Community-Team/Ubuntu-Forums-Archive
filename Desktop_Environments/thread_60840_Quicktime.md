---
title: "Quicktime?"
date: 2005-08-29
forum: Desktop Environments
---

### Post by Zodiac on 2005-08-29
NEVERMIND!

---

### Post by usererror on 2005-08-29
no wait! where'd you install it from?  :-#

---

### Post by Zodiac on 2005-08-29
Okay new problem... 

The video plays in Totem, but only if I open Totem and then select the file itself...

If I double click on the file I get the following error:

Couldn't Display "/home/me/movies/house_of_cosbys.mp4"

What is going on ya think??? Any idears?

---

### Post by arnieboy on 2005-08-29
[QUOTE=Zodiac]Okay new problem... 

The video plays in Totem, but only if I open Totem and then select the file itself...

If I double click on the file I get the following error:

Couldn't Display "/home/me/movies/house_of_cosbys.mp4"

What is going on ya think??? Any idears?[/QUOTE]
right click on file, select properties, click on the "open with" tab and select the default app u want to open it with.

---

### Post by Zodiac on 2005-08-29
[QUOTE=arnieboy]right click on file, select properties, click on the "open with" tab and select the default app u want to open it with.[/QUOTE]


I did that and I was getting a gigantic message about some security craziness... but just before I posted this I tried er again and it fired up.

So I am amped...

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

