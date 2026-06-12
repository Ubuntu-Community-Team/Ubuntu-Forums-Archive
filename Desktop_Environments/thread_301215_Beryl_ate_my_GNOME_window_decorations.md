---
title: "Beryl ate my GNOME window decorations"
date: 2006-11-16
forum: Desktop Environments
---

### Post by lowracer on 2006-11-16
Booted back into GNOME after playing with beryl/xgl.  Now I can't move or resize any windows because the top part you'd grab to move them with is gone.  Along with it the minimize, resize, and close buttons.  Any ideas how to restore my GNOME to full usefulness again?

---

### Post by ravisraval on 2006-11-16
make sure beryl-manager is running - if not, terminal-> "beryl-manager"
then you should get your stuff back... other wise, reboot x and turn off beryl by killing the process

---

### Post by robgill on 2006-11-17
If that dosen't work, try

```
beryl-manager && emerald --replace
```

assuming your using emerald instead of metacity

This works when that happens to me.

---

### Post by NiksaVel on 2006-11-17
this sounds a bit like the bug that loads emerald multiple times and has them conflicting...   I have it all the time and it's a known bug...

try "killall emerald" and than in beryl manager select a window manager or reload current...

---

### Post by ciscosurfer on 2006-11-17
> **lowracer said:**
> Booted back into GNOME after playing with beryl/xgl.  Now I can't move or resize any windows because the top part you'd grab to move them with is gone.  Along with it the minimize, resize, and close buttons.  Any ideas how to restore my GNOME to full usefulness again?Try issuing **gnome-settings-daemon &** in a terminal or add it to your startup sessions as **gnome-settings-daemon** (no backgrounding, i.e., no '&')

Also, you can use the ALT key to drag you windows back to sanity.  Hold the ALT key and with your cursor, drag the window away from the edge.

---

### Post by engineer on 2006-11-17
if beryl doesn't work, switch back to metacity.

get a terminal and type

```

metacity --replace

```

---

### Post by lowracer on 2006-11-17
thanks for all the help.  I tried different and bad stuff that ultimately hozed my system up good and tonight I'm reinstalling Edgy from the liveCD.

---

### Post by rax_m on 2006-11-17
Hi 

I've coincidentally managed to muck up my desktop with the same problem today. :(

When i log in i don;t get any window decorations. 
If I type in "metacity --replace" that works only for my current session...
how do i get it to work permanently. 

any help would be much appreciated. 
Thanks
Rax

---

### Post by rax_m on 2006-11-17
managed to fix it.. well with my particular way of fixing things ;)
i re-installed compiz using synaptic and that seems to have got my window decorations back permanently.
I did try running beryl/emerald again but it messed up my settings again..
so another quick re-install of compiz and it was all working again. 

I miss the effects of beryl tho'.. hopefully i'll get it working again.

---

