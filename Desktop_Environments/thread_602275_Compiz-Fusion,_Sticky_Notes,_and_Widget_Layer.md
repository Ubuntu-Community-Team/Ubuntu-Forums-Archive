---
title: "Compiz-Fusion, Sticky Notes, and Widget Layer?"
date: 2007-11-04
forum: Desktop Environments
---

### Post by cb474 on 2007-11-04
Is there any way to make the Gnome panel applet Sticky Notes appear in the Compiz-Fusion widget layer? I much prefer Sticky Notes to the similar features found in Screenlets and Gdesklets. I just would rather have them appear in the widget layer than on my desktop (I find it annoying how the sticky notes are always all there on my desktop at startup, but it would be great to have them just appear with the press of a hotkey).

---

### Post by madcow72 on 2007-11-04
Check out [this Howto]("http://ubuntuforums.org/showthread.php?t=589403&highlight=compiz+widget+layer").  I think I had the same issues as you, but this takes my sticky notes to the widget layer, which I control by hitting F9.

---

### Post by cb474 on 2007-11-04
Thanks, I tried this but it doesn't seem to work. What command do I put in the Widget Windows box in the Widget Layer preferences. I tired:

name=stickynotes_applet

and:

name=/usr/lib/gnome-applets/stickynotes_applet

Again, I'm trying to use the regular sticky notes that come with Gnome in the Compiz-Fusion Widget Layer, not the sticky notes that are part of Screenlets.

---

### Post by joeindio on 2008-03-19
Try this:

In the Compiz Fusion preferences, go to **Desktop > Widget Layer > Behaviour** and then set  Widget Windows to:

> (class=Stickynotes_applet & (title=^0 | title=^1 | title=^2 | title=^3))

This tells compiz to place all Stickynotes windows on the Widget layer (class=Stickynotes_applet) BUT filter only the ones whose names start with 0,1,2 or 3 (the notes), thus excluding the SN popups and preferences dialogs.

For me it works ok, the only minor drawback is that when I create a new note it goes to the Widget layer and I'd prefer to have it first on the normal desktop

---

### Post by fictivetoast on 2008-03-23
Try using :
(class=Stickynotes_applet) 

It works perfectly for me - for whatever reason, the prans seem to make the difference.  :)

---

