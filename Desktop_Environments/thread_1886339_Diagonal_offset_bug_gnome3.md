---
title: "Diagonal offset bug gnome3"
date: 2011-11-24
forum: Desktop Environments
---

### Post by samg34 on 2011-11-24
Videos of this really weird bug (via dropbox):
[here]("http://dl.dropbox.com/u/33591459/bug1.webm") and [here]("http://dl.dropbox.com/u/33591459/bug2.webm")

I installed the default gnome 3 on the default 11.10 (using sudo apt-get install gnome-shell). No custom builds. Nothing special. I first noticed some of my menus turning diagonally. Then I found that entire windows turn diagonally and so do the scroll bars and even the ctrl show mouse has a funky diagonal offset. (Watch the video).

This might be a graphics card problem. It is pretty weird. I run 32 bit gateway NV-53 with VESA: RS880M graphics card on Experience: Standard according to the "System Info" in the control panel.

Does anybody else have this bug? Where should I report it? How do I fix it?

---

### Post by samg34 on 2011-11-26
Reinstalling gnome3 seemed to fix it.
I think it has something to do with running a proprietary driver. This means the gnome team can't really develop the best possible product.
Does anybody know where I should report the bug so that gnome employees can fix it?

---

### Post by Potters Son on 2011-12-30
I'm getting the same problems as you; it appears that it happens sporadically when resizing windows.

To boot, Gnome Shell crashes frequently as well.

I reinstalled Gnome 3 (sudo apt-get remove gnome-shell -y && sudo apt-get install gnome-shell gnome-tweak-tool -y), and not only do I still have the problems above, but the screen goes glitchy when I hover over "Activities".

EDIT: I installed the latest AMD driver (version 11.12) from AMD's website earlier to make the characters stop glitching.

---

### Post by DGINSD on 2012-02-12
> **Potters Son said:**
> I'm getting the same problems as you; it appears that it happens sporadically when resizing windows.

To boot, Gnome Shell crashes frequently as well.

I reinstalled Gnome 3 (sudo apt-get remove gnome-shell -y && sudo apt-get install gnome-shell gnome-tweak-tool -y), and not only do I still have the problems above, but the screen goes glitchy when I hover over "Activities".

EDIT: Installed the latest AMD driver (version 11.12) from AMD's website earlier to make the characters stop glitching.

Just curious I have the same bug (diagonally distorted drop downs and tool tips) though it's rather random, most are fine but I get a few that consistently do it. Unity doesn't display the issue that I've noticed. Gnome shell hasn't crashed on me yet either. I have an HP Pavilion G6-1D60US with the AMD radeon graphics.

Just curious how did u get the drivers updated from AMD? 

A side note I'm not using either of the additional drivers listed when I tried the system hung on reboot.

---

