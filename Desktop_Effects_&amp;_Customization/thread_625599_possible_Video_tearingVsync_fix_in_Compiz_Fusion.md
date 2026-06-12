---
title: "*possible* Video tearing/Vsync fix in Compiz Fusion"
date: 2007-11-28
forum: Desktop Effects &amp; Customization
---

### Post by mukiex on 2007-11-28
This solution aleviated video tearing problems for me while running mplayer in Compiz. YMMV, and I'd love to hear about *how much* it varies. Hence the topic.

So I think I've found the solution [here](http://smspillaz.wordpress.com/2007/10/18/unlocking-the-full-video-potential-of-your-video-card/).

Here's the quick MukiScript edition :
```

#!/bin/sh
mkdir -p ~/bin/temp/
cd ~/bin/temp/
wget http://www3.mplayerhq.hu/MPlayer/releases/MPlayer-1.0rc2.tar.bz2
tar xvf MPlayer-1.0rc2.tar.bz2
cd MPlayer-1.0rc2/libvo/
wget http://smspillaz.googlepages.com/mplayrepatch.patch
patch -p0 vo_xv.c mplayrepatch.patch
cd ..
./configure
make -j 2
sudo cp /usr/bin/mplayer /usr/bin/mplayer-old
sudo cp mplayer /usr/bin/mplayer

```

As always, save it as a text file, make it executable and run it from the terminal. You'll need sudo rights to do this, or you can delete the last two lines. As an alternative I Rapidshared a zipped copy of the compiled executable (Ubuntu Gutsy, x86-32) which you can get [here](http://rapidshare.com/files/72837177/mplayer.zip). 

Once installed, double-check that Vsync is turned in in the "Display Settings" tab of the "General" section of Compiz Settings Manager (run "ccsm" from the terminal or run box). Voila! You should have compiz-friendly video! It won't flicker when you resize, it should vsync properly, and it should be less of a performance hog.

Good luck!

---

### Post by mukiex on 2007-11-28
Used it s'more, here's some observations I noticed :

- Still tears a little. That's annoying, I'm not quite sure how to fix this.
- In full-screen, it seems to ignore monitor-aspect. e.g. it fills my monitor with the video regardless. Annoying for movie trailers.
- Performance is higher than I've ever seen in mplayer, let alone under compiz. A video I keep handy as a benchmark for mplayer performance (audio-video sync on it always dies within the first 10-20 seconds) kept its a/v sync throughout.

---

