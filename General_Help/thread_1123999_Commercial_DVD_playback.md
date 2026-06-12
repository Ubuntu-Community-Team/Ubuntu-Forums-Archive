---
title: "Commercial DVD playback"
date: 2009-04-12
forum: General Help
---

### Post by Prof.Arronax on 2009-04-12
I am able to play back DVD video files from hard disk with *some* of the movie player type apps.  However, I've not been able to play much of anything from a commercially produced DVD (e.g., National Treasure, National Treasure 2, A Night at the Museum, etc.) Various errors including something about seek error or no response whatsoever from the movie player application, be it the default "Movie Player", its xine counterpart or MPlayer Movie Player.

Is there some sort of commercial decoder or codec that is required?

Thanks in advance!

---

### Post by lisati on 2009-04-12
Have a look here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by mb_webguy on 2009-04-13
In a nutshell, you need to add the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository to your Software Sources, and install the libdvdcss2 package.  This allows Linux media players to bypass the copy-protection used by many commercial DVDs that otherwise prevents those discs from being played.

---

