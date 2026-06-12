---
title: "MPlayer slowed down after upgrade"
date: 2006-06-03
forum: Desktop Environments
---

### Post by serras on 2006-06-03
Two days ago I upgraded from Ubuntu 5.10 to 6.06, via the Update Manager. Everything went OK, except for MPlayer and VLC. Both of them now work horribly slow. I don't know what may have happened :-(
I there any way to improve the performance and get the one I was accostumed to? As a note, I used prelink but now I've disabled it.

---

### Post by mpierce on 2006-06-03
I noticed the same thing. A check showed some libraries were outdated or missing. I recompiled the source code and it's working perfectly but with a trick so that the correct libraries and other files were installed and updated by apt on demand:

   sudo auto-apt run ./configure --enable-gui
   sudo auto-apt fakeroot debian/rules binary

I then installed the new binary which was built:
   mplayer_1.0cvs_i386.deb

Everything works perfectly!
Make sure you have installed the auto-apt package so that it'll update those *.h files that mplayer requires.

Hope this helps.

---

### Post by serras on 2006-06-03
The commands you tell just doesn't work (the first one does, the second doesn't). I recompiled the entire MPlayer, but it stills is very slow when I show it fullscreen (at normal size it is OK).

---

### Post by snegoviK on 2008-05-30
Sorry. I didn't notice this is archive. This post can be deleted.

---

