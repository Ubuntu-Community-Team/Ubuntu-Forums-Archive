---
title: "my mplayer suddenly became slow"
date: 2009-06-11
forum: General Help
---

### Post by bummm on 2009-06-11
I use mplayer exclusively, no matter what format movie I open up it pops up instantly, very happy with it.

but as of recently it takes about 10 seconds to open up a movie, whats going on? how can I fix it?

thank you

---

### Post by bummm on 2009-06-11
I removed mplayer, then installed it again, didnt help :(

---

### Post by Soul-Sing on 2009-06-11
You could try to remove your ./mplayer. But it is not likely this works....

---

### Post by bummm on 2009-06-11
solved, my mplayer is now back up to speed

this is what I did, it might help somebody else:


I disabled    stop-xscreensaver = "yes"       in etc/mplayer/mplayer.conf

Im not using a screensaver, and mplayer complained it couldnt find it, so i guess that might have been it , victory!

---

