---
title: "Sound fixed"
date: 2008-11-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by armandh on 2008-11-16
this posted by another worked great for me when using stock 8.10
there are screenshots in the catch up post
--------------------------------------------------------------------------------

In a terminal type:
sudo gedit /etc/modprobe.d/alsa-base

At the end of alsa-base file add:
options snd-hda-intel model=dell

[save] i add editorially

Reboot your Mini
[In a terminal type: sudo reboot]

After logging in, double click the volume icon and turn your speaker volume up.



All Credit goes to [www.ubuntumini.com](www.ubuntumini.com)

---

### Post by N74JW on 2009-03-04
Thanks, but that did nothing to enable sound on my Mini.  I am running a full update to see if that helps...

---

### Post by gen3ric on 2009-03-10
> **N74JW said:**
> Thanks, but that did nothing to enable sound on my Mini.  I am running a full update to see if that helps...

Try double clicking on the sound icon in the menu bar. In the speaker section, make sure it's turned up.

---

