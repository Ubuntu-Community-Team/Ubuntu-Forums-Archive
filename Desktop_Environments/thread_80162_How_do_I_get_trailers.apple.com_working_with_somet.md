---
title: "How do I get trailers.apple.com working with something other than MPlayer?"
date: 2005-10-21
forum: Desktop Environments
---

### Post by mjukr on 2005-10-21
I've tried to get the embedded movie trailers at [http://trailers.apple.com](http://trailers.apple.com) to work with xine, gstreamer, and mplayer, and have only been completely successful with mplayer using these steps:

[http://www.ubuntuforums.org/showthread.php?t=76946](http://www.ubuntuforums.org/showthread.php?t=76946)

I would really like to get it working with xine (and hopefully gstreamer in the future). Has anyone had luck getting trailers on this site (or any others) to work with totem-xine *without* any firefox extensions?

So, my question is really "how did you get embedded media to play" and not "how do I get embedded media to play." Like I said, it's working just fine with MPlayer, but I'm curious as to other options not relying on firefox extensions.

---

### Post by Blackie_Chan on 2005-10-21
I have totem-xine installed, and was able to play embedded vids by just installing mozplugger by running:
```
sudo apt-get install mozplugger
```
My only problem so far is that I haven't installed a codec to play *.mov files yet.

---

