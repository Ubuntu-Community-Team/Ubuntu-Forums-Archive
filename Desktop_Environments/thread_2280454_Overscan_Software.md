---
title: "Overscan Software?"
date: 2015-05-30
forum: Desktop Environments
---

### Post by Sillyname on 2015-05-30
My Ubuntu desktop stretches outside the HDTV window.  The HDTV has limited settings to compensate.  Is there software out there that will shrink down the desktop so I can see it all?

Thanks in advance,

Stephen

---

### Post by RobGoss on 2015-06-01
Sound like you need to adjust the resolution on that HDTV

---

### Post by oldfred on 2015-06-01
I just changed TV to best fit and that worked.

---

### Post by papibe on 2015-06-01
Hi Sillyname.

You may be able to do something, depending on the graphic driver you are using.

Could you open a terminal, run these commands, and post back the results (you can copy/paste the output)?
```
lspci -nnk | grep -iA2 vga
 
xrandr -q

xrandr --q1
```
Regards.

---

### Post by Lee_Henderson on 2015-08-18
Im having the same issue, but the TV has no options to cure this, its a cheep TV.  Is there any software to control this?

---

