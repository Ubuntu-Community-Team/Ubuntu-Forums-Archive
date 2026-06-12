---
title: "Compiz works but bad performance after reboot"
date: 2007-04-28
forum: Desktop Effects &amp; Customization
---

### Post by lithium on 2007-04-28
EDIT: I found the bug! It's unreleated to compiz after all, it's evolution-data-server taking up 50% of CPU power... now only if I knew why it does this, after compiz is activated...

---

Hi,

I upgraded my sister's computer to feisty. Worked mostly okay and when I enable compiz using the desktop effects panel it works, too (using the nvidia-glx shipping with feisty with a geforce4 card).

The problem is that some seconds (or minutes) after compiz is started, performance drops to HORRIBLE levels, to a point where dragging a window doesn't show the movement at all. If taht happens, mouse movement is still nice but not window movement, fades, cube rotation etc. Then, after another few seconds it works nice again, but only for a very shot time, then it gets very laggy again.

I used compiz on this PC for over half a year myself (a version I compiled myself) and then it worked flawlessly!

Any idea what could cause this? Anyone seeing something similar?

---

### Post by lithium on 2007-04-29
I noticed that the "nvidia" module is using the "agpgart" module, IIRC it should be better to use NVidia's buildin AGP support? How can I force the use of that?

---

### Post by lithium on 2007-04-29
After starting compiz --replace I see the following btw:

/usr/bin/compiz.real: pixmap 0x16000cf can't be bound to texture
/usr/bin/compiz.real: Couldn't bind redirected window 0x120018f to texture

EDIT: looking on google, this seems to be a problem that normally makes
windows etc white... but it doesn't do that here, it LOOKS great, only
SLOOOOOOW.....

---

