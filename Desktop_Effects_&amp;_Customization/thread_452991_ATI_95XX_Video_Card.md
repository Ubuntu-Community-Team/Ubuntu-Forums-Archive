---
title: "ATI 95XX Video Card"
date: 2007-05-23
forum: Desktop Effects &amp; Customization
---

### Post by ironmike on 2007-05-23
I have an ATI Radeon 9550 graphics card and I am running Feisty Fawn 7.04. What is the best driver to use to get a 3D desktop to run? I want to run Beryl and Emerald. Now, just so you know, I attempted some of this already and messed it up so bad I had no graphics and had to re-install the Ubuntu. Any help would be great. I am pretty new to Ubuntu and as much guidance that can be provided would be great.

---

### Post by medicineman24 on 2007-05-23
Hey I have the same graphics card. And use to have the same problem.  I probably cannot help but I will try in about 10 minutes.  Hold on.

---

### Post by medicineman24 on 2007-05-23
Ok I can only tell you that I am currently using the ati proprietary driver available on their own site [http://ati.de/support/driver.html]("http://ati.de/support/driver.html").  I also made sure that the default fglrx driver was uninstalled using the Add/Remove programs.  Somehow, after a week of messing around, I got the driver working properly and direct rendering enabled (check with: glxinfo | grep direct ) in the terminal.  I wish you luck. Sorry I can't help much.
 BTW I followed countless how to's and none of them worked like a charm.

---

