---
title: "How can I move the VisualBoyAdvance.cfg file to ~/.vba?"
date: 2010-06-09
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2010-06-09
Hi.
How can I move the VisualBoyAdvance.cfg file to ~/.vba
Everytime I start VBA Express, it forces me to have the VisualBoyAdvance.cfg created in my home directory, while ~/.vba is lying empty!

---

### Post by Contrast on 2010-06-09
I ran into this problem with a little game called Spheres of Chaos. Short of editing the source code of the program, there's not really a *proper* way of doing this as far as I know, but the following [admittedly hack-ish] method works fine for me:

I just wrote a very simple script which moves the config file to where the program expects it to be (no dot), starts the program, then moves the config file back (with dot) when the game exits. Alt+F2 -> gksu gedit -> paste the following:
```
#!/bin/bash
mv "$HOME"/.vba/VisualBoyAdvance.cfg "$HOME"/VisualBoyAdvance.cfg
vba "$@"
mv "$HOME"/VisualBoyAdvance.cfg "$HOME"/.vba/VisualBoyAdvance.cfg
```
Save it as /usr/local/bin/vba.sh, then make it executable (Applications -> Accessories -> Terminal -> sudo chmod 755 /usr/local/bin/vba.sh). Now you just need to edit the menu entry so it points to your script.

---

### Post by Rytron on 2010-06-09
Cheers Contrast.

---

