---
title: "Amarok skips all songs =("
date: 2006-08-20
forum: Desktop Environments
---

### Post by Aikon- on 2006-08-20
I recently installed Amarok because I've heard great things. The interface is certainly very appealing compared to clunky (and not to mention ugly) systems like XMMS.

Unfortunately, I'm having some problems. I went through the initial config, choosing my media folders and let Amarok import my 6000 or so mp3s into its library (or "collection", as you like to call it ;). When I drag a folder or some song files or whatever onto the playlist, they move over just fine. But when I actually try to play one, the OSD shows the song name and artist and then it moves on to the next song, as if the song length were 0 seconds. Doesn't actually play any sound, and repeats this through to the end of the playlist. No error message, no crashing, and it does add the songs to the recently played list and increments their play count.

Suggestions? I would really like to get this resolved as it looks like a far superior media player / library than anything else I've tried in Linux so far.

My system:
OS: Ubuntu 6.06 (all the latest updates)
DE: GNOME (I had to install kdelibs when installing Amarok through Synaptic)
Engine: xine (libamarok_xine-engine version 1 framework version 15)
Ouput plugin: ALSA (has been working fine with Totem, MPlayer, XMMS, etc.)
Amarok: 1.3.9 (from the Ubuntu repositories)

If you need any more informaion please let me know..

-Aikon

---

### Post by dasunst3r on 2006-08-20
It appears that you have not installed MP3 support.  To enable multimedia support, look up Automatix or Easy Ubuntu on this forum.

---

### Post by LinLenLap on 2006-08-26
**UPDATE:**

I found the solution on this thread: 

[URL="http://www.ubuntuforums.org/showthread.php?t=189305&highlight=amarok+skips+playlist"]http://www.ubuntuforums.org/showthread.php?t=189305&highlight=amarok+skips+playlist
[/URL]

Essentially, go to synaptec and search for xine. Install the gstreamer plugin.

Restart Amarok.

**ORIGINAL:**

> **dasunst3r said:**
> It appears that you have not installed MP3 support.  To enable multimedia support, look up Automatix or Easy Ubuntu on this forum.

Perhaps that is the case, but I do have multimedia mp3 support, xine engine, amarok and ubuntu, and I have the same problem as OP.

Best,

LLL


Also, sorry to above

---

### Post by raven65az on 2006-08-26
Make sure you have Xine extra codecs installed

---

