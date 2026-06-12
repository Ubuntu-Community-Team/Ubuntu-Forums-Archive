---
title: "Nautilus font size in listview"
date: 2010-06-06
forum: Desktop Environments
---

### Post by abunty on 2010-06-06
Hi,

When zooming to 100% in listview the font gets huge, but only in the listview panel (see image). 

Does anybody know where to reconfigure this to normal behaviour (I'd  like the 100% fontsize to be the same as in the treeview in the left panel).

I had this behaviour already with the previous relase of Ubuntu, and upgrading to 10.04 did not solve the problem.

Help is very much appreciated!

---

### Post by abunty on 2010-08-29
Nobody???

---

### Post by AndyBoy_LV on 2011-04-03
Would really like to know if you have been able to solve this problem :) Because otherwise my Nautilus looks ugly with these oversized fonts :(

---

### Post by vanadium on 2011-04-03
Select View - Normal size or press Ctrl+0

---

### Post by ejuke on 2011-07-08
> **AndyBoy_LV said:**
> Would really like to know if you have been able to solve this problem :smile: Because otherwise my Nautilus looks ugly with these oversized fonts :sad:

This was annoying me as well - for at least 2 years. To be clearer  about the issue, when the icon size between panes is the same, the fonts in the  listview pane are smaller than the fonts in the treeview pane. I can't  imagine that it wasn't noticed during development as, unlike a bug that  only happens under certain conditions, this issue is in your face all  the time. I'm guessing it was just never thought to be an issue, or a  bug, but probably more of a preference - if there was any thought about  it at all.

To solve the problem, I actually downloaded the source  code, made some changes and recompiled. After that, font and icon sizes  were consistent between panes. In one way, it's nice to know the source  code is available. I'm guessing it took me about an hour to poke around  and figure out what changes needed to be made. It wasn't too difficult  to edit and recompile, but in my opinion it really shouldn't have been necessary. I  did this about 2 years ago. However, for the last year, I've been using  KDE and Dolphin. I may still have the source code for Nautilus though.  If you're really interested, I can probably post the changes and then  you can do the same.

On a side note, and not a show stopper for  me, the recompiled executable was a bit larger than the original  distributed one. Perhaps this is typical - I don't know. I didn't change  any config or make files and I can't imagine that everything was  statically linked, but who knows - I don't claim to be a seasoned hard  core C/C++ programmer. I'm sure there are ways to optimize the binary -  I'm guessing it's not configured to do so by default.

---

