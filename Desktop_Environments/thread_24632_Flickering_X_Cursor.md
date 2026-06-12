---
title: "Flickering X Cursor?"
date: 2005-04-07
forum: Desktop Environments
---

### Post by forcotton on 2005-04-07
I've just got a nvidia card  :D and soon after installation I noticed the flickering cursor in X. Well I went through documents... turns out its hardware cursor in the nvidia driver. But when I turn off hardware cursor, graphics are crappy in blender ( an opengl app which I'm trying to learn ) . 
Since the flickering only occurs with animated cursor, is there a easy way to get rid of it? I mean just to remove the animation... I like that little white arrow, and hand, and resize bar etc....

---

### Post by Nis on 2005-04-07
[QUOTE=forcotton]I've just got a nvidia card  :D and soon after installation I noticed the flickering cursor in X. Well I went through documents... turns out its hardware cursor in the nvidia driver. But when I turn off hardware cursor, graphics are crappy in blender ( an opengl app which I'm trying to learn ) . 
Since the flickering only occurs with animated cursor, is there a easy way to get rid of it? I mean just to remove the animation... I like that little white arrow, and hand, and resize bar etc....[/QUOTE]
 Check out the different cursor themes [here](http://gnome-look.org/content/show.php?content=14484).  You can use gcursor (install with Synaptic) to install and change your mouse theme.  I'm sure there's some theme there that isn't animated.  Whiteglass, which comes with X, is a nice non-animated theme.

---

### Post by forcotton on 2005-04-10
I finally found this: [http://varg.dyndns.org/psi/pub/code/xcurs/](http://varg.dyndns.org/psi/pub/code/xcurs/)
and removed the animation in jimmac's cursor theme. It's interesting that I still feel that small clock are moving even though it's just the first frame ;)

---

### Post by szr4321 on 2005-08-25
@forcotton: Thanks a lot for the hint!
For others experiencing the same problem:
Get [xcurs](http://varg.dyndns.org/psi/pub/code/xcurs/) and remove all the animations of the cursors in /usr/share/icons/Human/cursors.
(Don't forget to make a backup before and remember that only root got write access there.)

---

