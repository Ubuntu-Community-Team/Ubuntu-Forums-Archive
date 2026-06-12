---
title: "Steam 64-bit crashes on store pages with video"
date: 2013-07-14
forum: Gaming &amp; Leisure
---

### Post by oldrocker99 on 2013-07-14
Ah, the joys of Googling.

I had been extremely frustrated with Linux 64-bit Steam crashing on every store page that had a video.

Go to [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

and make sure you're downloading the **32-bit** version of Flash and get the .tar.gz version.

make a new directory in  ~/.steam/bin called plugins

Extract the libflashplayer.so to ~/.steam/bin/plugins and restart Steam. No more crashes!

---

### Post by silbar on 2013-07-14
Did not work for me.  I had to create ~/.stream/bin/plugins and put the lib*.so there.  But, on starting two or more pages with Flash videos running simultaneously, I still get multiple crashes.

Richard Silbar

---

### Post by Ranko Kohime on 2013-07-17
There's a 64-bit version of Steam?  I was under the impression that it was 32-bit only.

(Or are you implying it crashes on 64-bit systems?)

---

### Post by oldrocker99 on 2013-07-17
Steam is supporting 64-bit (it says here), but to tell the truth, I don't know whether my desktop is running the 32 or 64 bit Steam client. I only passed along the fix that had worked for me.

---

### Post by Ranko Kohime on 2013-07-19
I still can't run it without ia32-libs, so I'm guessing it's still 32-bit, regardless of what it claims.  :)

---

### Post by oldrocker99 on 2013-07-19
Yeah, it does need ia32-libs; you're right. I do notice that in Windows, all the team downloads are 32-bit. I read that Steam was releasing 64-bit binaries, but it hasn't been confirmed.

---

