---
title: "startx vs. startxfce"
date: 2006-07-25
forum: Desktop Environments
---

### Post by gary800 on 2006-07-25
I'm building an old toshi notebook (1gz, 256mb).

I built the OS using the server verison of 6.06 and apt-get installed xubuntu-desktop.

The goal is the smallest OS foot print with office, brower, mail, video, mp3 and VOIP softphone.

I've disabled gdm at boot up and start the x session by the startxfce4 command. I then tried startx instead. Oddly, the are a few differances between the desktop depending on the command used.

startxfce4 is slower and uses the font sans 9.

startx is faster but has crashed watching a movie and uses the font sans 10.

Any idea why this is?

---

### Post by loell on 2006-07-25
try restoring gdm, i think it has no effect on performance and very little if any.

---

