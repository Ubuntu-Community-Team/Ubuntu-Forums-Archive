---
title: "pixelated playback on totem"
date: 2005-10-17
forum: Desktop Environments
---

### Post by mangoshake on 2005-10-17
**Problem:**
I grabbed xine-ui and totem-xine along with a handful of codecs including w32codecs, but when I'm trying to watch video files, the playback is horribly pixelated. They play fine in xine, but I would really like to get totem to work as well.

**What I did:**
- got my Radeon 9800 pro working on fglrx 8.16.20 [this way]("http://ubuntuforums.org/showthread.php?t=76057").
- installed xine-ui and totem-xine.
- grabbed a couple of gstreamer codecs (I didn't get them all, only the ones that I think I'll use, but does it even matter now that I'm using totem-xine and not totem-gstreamer?)
- grabbed w32codecs [here]("http://ubuntuforums.org/showpost.php?p=411934&postcount=12")
- tried playback in totem => pixelated
- tried playback in xine => looks good
- tried playback in xine with "deinterlace_by_default" turned on => looks just like without
- tried playback in totem with "View > Deinterlace" checked => still pixelated as ever
- switch default video sink in "System > Multimedia Systems Selector" between XWindows (X11/XShm/Xv) and XWindows (No Xv) => same

**Questions:**
- How can I get totem to play files with the same quality as in xine and not pixelated?
- How come the deinterlace option in totem doesn't seem to be doing anything?
- Do I still need the gstreamer stuff if I'm not using totem-gstreamer? What other applications might use it? Just out of curiosity, not that I'm gonna remove them
- what do the different video sink options (X11/Shm/Xv/No Xv/SDL) mean?

---

### Post by bluck on 2005-10-17
personally, i hate totem :)

i use vlc to play almost all my media, some things like mplayer a little more, such as wmv files.

i know this doesnt help...  but i had to put in my two bits. ;)

---

### Post by mangoshake on 2005-10-18
bump.

Also I looked around some more and read something about xvinfo. 

Output from xvinfo:
```

X-Video Extension version 2.2
screen #0
 no adaptors present

```

Is that the/a problem?

---

### Post by mangoshake on 2005-10-18
[QUOTE=bluck]
i use vlc to play almost all my media, some things like mplayer a little more, such as wmv files.
[/QUOTE]

I used to have mplayer on the old Hoary install, and I've also tried vlc on Windows. Both are good powerful players, but unfortunately both look ugly (has always been for mplayer; as for vlc, [see here]("http://ubuntuforums.org/showthread.php?t=76122&highlight=ugly+vlc")). I know this is a stupid reason not to use these perfectly fine media players, but I like preserving a generally consistant (nice) look across my system.

---

