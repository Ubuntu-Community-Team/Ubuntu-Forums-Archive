---
title: "Terminal fonts funky after font installation"
date: 2007-05-22
forum: Desktop Environments
---

### Post by Enverex on 2007-05-22
I was searching for a bug in something else earlier today and remembered that I have very few fonts installed, so I did a search for ttf-* and installed, well, pretty much everything in Synaptic that was actually a TrueType font matching that... only problem is that after installing them my Terminal font is now screwy (as is the one used by Synaptic to show terminal output, but because of that one being smaller it's even worse and barely readable).

The "before" picture is taken on my laptop which is set to the same font and size (Monospace 12) as I obviously can't show my main PC before hand.

So, any ideas? (it would be a pain to figure out which 60 or so font packs I installed and this must be a bug anyway so best to fix it).

Left to right:

How terminal used to look and should look > How it looks now > How synaptics term looks.

---

### Post by Enverex on 2007-05-24
Bump. I think I'll file a bug for this anyway though.

---

### Post by kenthomson799 on 2007-06-01
Confirmed. I too have the same problem.
Enverex if you find a solution please PM me

---

### Post by Enverex on 2007-06-02
I did find the problem.
There is a font package that replaces the Monospace font with another Monospace font. You need to remove ttf-georgewilliams.

---

