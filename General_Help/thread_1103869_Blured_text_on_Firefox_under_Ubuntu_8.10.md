---
title: "Blured text on Firefox under Ubuntu 8.10"
date: 2009-03-23
forum: General Help
---

### Post by de049 on 2009-03-23
Hi all,

I have been using my Ubuntu 8.10 happpily for the past few weeks, but one thing i cannot get over is that on Firefox, text sometimes comes up very blurred (unreadable).  If i highlight the text with my mouse, it clears up and becomes readable.  It happens on 1 of every 3 websites i visit.

Please see attached file for an example of how it looks.  I have my display drivers rightly set and the Monitor is also picked up ok.  So i cannot see it being that.  Refresh rate set to 60Hz as on the monitor.

Tried resizing fonts and zoom parameters on Firefox to no avail.

Any ideas?

thanks guys

de049

---

### Post by kerry_s on 2009-03-23
looks like a bitmap problem, run> 
**sudo dpkg-reconfigure fontconfig-config**

say no to bitmap fonts, then just restart X

---

### Post by de049 on 2009-03-23
thanks for that.  Its fixed now!

;-)

---

