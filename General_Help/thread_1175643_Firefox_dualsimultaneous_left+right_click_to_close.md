---
title: "Firefox dual/simultaneous left+right click to close tab (broken)"
date: 2009-06-01
forum: General Help
---

### Post by Jays on 2009-06-01
Hi,

I've just got a clean install of 9.04, with all the latest updates. One thing I'm missing is (previously, on 8.10) the version of Firefox would allow me press the left+right mouse clicks simultaneously in order to close a tab.

I did Google for a quite a bit, but I couldn't see anything. Is there an about:config flag for this?

Thanks!

Jay

P.S. Apologies if this is in the wrong forum.

---

### Post by Jays on 2009-06-02
Just an interesting update I found:

If I "Restore a session", the dual-click thing works for the tabs that are restored. The second I open a new tab, the functionality breaks.

A bug?

Thanks.

---

### Post by jonathanysp on 2009-06-02
the right+left click to emulate a middle click should be a setting in the xorg.conf file if not wrong. It isnt a function within firefox. can you middle click with left+right in other programs?

---

### Post by Jays on 2009-06-02
> **jonathanysp said:**
> the right+left click to emulate a middle click should be a setting in the xorg.conf file if not wrong. It isnt a function within firefox. can you middle click with left+right in other programs?
I haven't really tried. The dual-click also use to activate the middle click's auto scroller (general.autoScroll) which also doesn't work now (just activates the right-click menu), and I've diffed my two xorg.conf's (8.10 and this one), and these are the only differences:

```
# diff /etc/X11/xorg.conf /media/disk/old/root/etc/X11/xorg.conf

20a21,24
> Section "Device"
>     Identifier    "Configured Video Device"
> EndSection
> 
29,33d32
<     DefaultDepth    24
< EndSection
< 
< Section "Module"
<     Load    "glx"
35,40d33
< 
< Section "Device"
<     Identifier    "Configured Video Device"
<     Driver    "fglrx"
< EndSection
< 

```Thanks for the input so far

---

