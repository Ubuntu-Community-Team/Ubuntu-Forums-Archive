---
title: "how can i make my dvi on nvidia card primary instead of vga?"
date: 2005-04-21
forum: Desktop Environments
---

### Post by martinez9049 on 2005-04-21
hi,
im running twinview in nvidia and i would like to make the lcd connected by dvi the primary monitor instead of vga. right now if i disable twinview and have both monitors connected the vga comes up. 

thanks,
ismael m

---

### Post by hobnob on 2005-04-21
I have a feeling that without twinview, you cannot change that. If there is a monitor connected to DSUB, the card will always default to that.

---

### Post by lewiz on 2005-04-23
[QUOTE=martinez9049]hi,
im running twinview in nvidia and i would like to make the lcd connected by dvi the primary monitor instead of vga. right now if i disable twinview and have both monitors connected the vga comes up. 

thanks,
ismael m[/QUOTE]
 I'm not entirely sure about this but try adding something like:

Option     "ConnectedMonitors" "DFP,CRT"

to your /etc/X11/xorg.conf and restarting gdm/X.

---

