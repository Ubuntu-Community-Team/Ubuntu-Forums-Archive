---
title: "Totem/Mplayer crash on all video files"
date: 2009-03-16
forum: General Help
---

### Post by boothruwindow on 2009-03-16
I'm getting to the point that I can do almost everything which I could ever do on in Windows (without spending a month trying to make it all work, ARRRRRGH, but at least I don't worry about security), but tonight was the first time I ever tried to launch a video from my own machine in Linux. This may be the most confusing thing I've dealt with yet.

Ubuntu has in it's default menu Applications > Sound & Video > Movie Player, which opens a window labeled Totem. Inside of the view window of Totem is a graphic for what seems to be another program, Mplayer. These both were on my computer before I did a clean install (folder delete and Synaptic reinstall, and since the current Mplayer folder contains nothing but graphical files and fonts, my best guess is that this is just a GUI. I did not notice this before I got the idea to remove the original MPlayer folder, do a Synaptic removal, and then do a clean install of MPlayer. I never touched Totem, here is the list for that folder:
/usr/share/totem$ ls
filmholes-big-left.png fullscreen.ui plugins.ui totem.ui
filmholes-big-right.png mozilla-viewer.ui properties.ui uri.ui
filmholes.png playlist.ui totem_logo.png video-list.ui

I observe now that I can launch from Sound & Video the Mplayer by itself, (with the real cool buttons), or Totem (from the Movie Player link), which displays Mplayer inside of it. Neither plays anything, but when I try to play something without the Totem window (not using the Movie Player link), Mplayer presents this error message, intead of crashing:
No stream found to handle url dvd://1
Looks like it won't even connect to my DVD player. Does any of this make sense at all?

Before and after I changed anything, I got the same in the Totem window. No matter what I try to play, be it streaming YouTube video, or MPEG and AVI from CDs, it did the same time each time I tried to launch any such file - it crashed, window disappeared, and that was it.

By the way, Synaptic may not have downloaded everything which it decided was needed when I did that reinstall - I got a negative message concerning that!

Heeeeeeeeellllllllllllp!!!!

Thanks.

Edit: Actually, attempts at playing YouTube don't cause a crash, at least now - I get the prompt to download codecs, which brings me to the same download page which I saw before I changed my original installation - the only choice was for "bad" codecs. With nothing else apparently available without charge, and totally disbelieving that Ubuntu would offer codecs that really don't work, an no idea where to look otherwise, I did install them - but I didn't do that this time around, because they didn't help me the first time.

boothruwindow is online now Report Post   	Edit/Delete Message

---

### Post by boothruwindow on 2009-03-16
:):)bump:):)

---

### Post by boothruwindow on 2009-03-17
:):)bump:):)

---

### Post by aeiah on 2009-03-17
i suggest installing the codecs and packages mentioned near the start of this howto:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

