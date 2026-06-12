---
title: "Beryl quality problems"
date: 2007-04-16
forum: Desktop Effects &amp; Customization
---

### Post by Blue Label on 2007-04-16
So I finally got the latest nVidia driver (1.0-9755) installed and followed all the outlined instructions for editing my xorg.conf file on the Beryl-Project wiki and  [http://technowizah.com/2007/02/debian-how-to-aiglx-beryl.html](http://technowizah.com/2007/02/debian-how-to-aiglx-beryl.html).  However, whenever I run Beryl, the overall quality of the desktop effects aren't what I'd expect considering what my laptop runs (see signature below).  My old desktop with 512 MB of RAM and a 128 MB GeForce 5200 runs Beryl much better.  What settings can I tweak to make everything run better?

---

### Post by SishGupta on 2007-04-16
> **Blue Label said:**
> So I finally got the latest nVidia driver (1.0-9755) installed and followed all the outlined instructions for editing my xorg.conf file on the Beryl-Project wiki and  [http://technowizah.com/2007/02/debian-how-to-aiglx-beryl.html](http://technowizah.com/2007/02/debian-how-to-aiglx-beryl.html).  However, whenever I run Beryl, the overall quality of the desktop effects aren't what I'd expect considering what my laptop runs (see signature below).  My old desktop with 512 MB of RAM and a 128 MB GeForce 5200 runs Beryl much better.  What settings can I tweak to make everything run better?

Turn off  refresh rate detection, set it manually to your refresh rate (NOT 200 like some people suggest), and i personally turn of vsync but then it will use up more cpu, but im dual coring it and dont care really.

All 3 of those settings should be found in the general options tab for beryl.

Also that how-to you followed kinda sucks. I dont use dbe or tripple buffering or no off screen pixmaps and everything runs fine on my end.

---

### Post by Blue Label on 2007-04-18
Thanks, everything works perfectly!

---

### Post by Beach on 2007-04-23
@SishGupta

Found this thread and fixed my Beryl speed issues - just wanted to say thanks man...

---

