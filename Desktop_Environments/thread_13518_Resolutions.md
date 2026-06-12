---
title: "Resolutions"
date: 2005-02-01
forum: Desktop Environments
---

### Post by wizzomafizzo on 2005-02-01
I was wondering how I can get the resolution on Ubuntu higher than 1024 x 648?
I'm using a Dell Latitude C600(I think?) laptop if that helps. I'd usually be fine with it except it makes using the touchpad very hard and I've grown use to a higher resolution.

Thanks in advance for any help.

---

### Post by rlw on 2005-02-01
Not very sophisticated but helpful for investigations:
Boot a Knoopix CD and check out what Knoppix chooses as resolution, maybe you'll have to set knoppix screen=1400x1024 at the boot prompt (atapt resolution to your needs).
Save the /etc/X11/XF86Config-4 file to use it as reference to modify yours on the ubuntu system, but do not replace the one on your system with the Knoopix file.
Compare the "Screen" and "Display" section and adapt.

---

### Post by machiner on 2005-02-01
This year I gave up sweets.

Oh - sorry, different RESOLUTIONs...

mu hahahaha

---

