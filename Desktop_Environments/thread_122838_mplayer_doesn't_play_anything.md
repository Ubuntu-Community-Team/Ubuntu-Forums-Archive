---
title: "mplayer doesn't play anything"
date: 2006-01-28
forum: Desktop Environments
---

### Post by Tilex on 2006-01-28
I've been trying to play video files with mplayer for a while now, and it doesn't work at all.  Everything was working fine before I upgraded to Breezy, but now no multimedia app opens a video file (xine, amarok, mplayer..).  I checked for the win32 codecs, and I have them installed.  However, when I open a file, I get the following error message:
```
error opening/initializing the selected video_out (-vo) device
```
Does anybody have a clue as to what might be the problem?

---

### Post by Neo Ex on 2006-01-28
Go in the preferences and change the output device in the Video tab. I've setted the gl2 and it works for me.

---

### Post by leemckusic on 2006-09-19
Apparently as part of the Upgrade from Breezy Badger the default codec has been changed for mplayer. A codec is the chunk of code that interprets your video file your display. There are different codecs for different kinds of input file and different kinds of video card and software. You can find a working codec by trial and error.

Start a terminal

Find the list of codecs like this: 
mplayer -vo help

Learn more about mplayer from the manual page:
man mplayer

Try to play a local file with a codec like this:
note gobs of info reported by mplayer as it starts.
mplayer -vo gl2 hpim0167.mpg 

Per the man page, the "default codec" is set in the file
/etc/mplayer/mplayer.conf

Editing this man page will require "sudo"
sudo vi /etc/mplayer/mplayer.conf

---

