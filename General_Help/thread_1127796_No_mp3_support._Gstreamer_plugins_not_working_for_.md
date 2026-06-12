---
title: "No mp3 support. Gstreamer plugins not working for Rhythmbox, Banshee"
date: 2009-04-16
forum: General Help
---

### Post by jermsie on 2009-04-16
After doing some google searching on the issue, I installed gstreamer plugins (w32 from medibuntu, good, ugly..) but this doesn't seem to have changed anything.

Rhythmbox (Failed to connect: Connection refused) and Banshee are not playing mp3's. However, VLC and MPlayer are but these are not programs suited for having music libraries/friendly playlists etc.

Note: Amarok 1.4.10 prompted me to install libxine1-ffmpeg, which allowed mp3s to play in Amarok ONLY.

How can I fix this mp3 problem, system wide? I'm running out of time as this isnt my computer but my mother's. Only a day or so left until I won't have any time to fix anything.

---

### Post by Redundant Username on 2009-04-16
Maybe you need restricted codecs from the package manager?

---

### Post by jermsie on 2009-04-16
> **Redundant Username said:**
> Maybe you need restricted codecs from the package manager?

ubuntu-restricted-extras and w32 codecs already installed.

---

### Post by jermsie on 2009-04-19
If anyone could suggest something I'd be grateful. I don't have much time left to fix these issues. It isn't my machine

---

### Post by jermsie on 2009-04-22
Don't know why, but Rhythmbox seems to be fine now.

---

### Post by trondhuso on 2009-04-30
I completely uninstalled Banshee and the gstreamer-plugins then installed 
ubuntu-restricted-extras and then installed Banshee. 
Now Banshee extracts to MP3 from CDs.

---

### Post by vässlan on 2009-07-30
something broke the mp3 support for me with gstreamer too, I couldn't even fix it, so i run gmusicbroswer now with mpg321

running jaunty 9.04 btw

---

