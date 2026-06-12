---
title: "XFCE: auto-hide panel not working"
date: 2006-12-13
forum: Desktop Environments
---

### Post by elektronaut on 2006-12-13
Hi,

my applications panel stops auto-hiding after a while and remains on top of application windows. Is this a bug? I also checked the margin settings, but they are set to 0.

---

### Post by automaticgiant on 2006-12-22
yeah i dont know whats going on there but mine started doing it too.  is pissing me off.  when you switch autohide on and off it acts like its hiding but to the wrong side of the panel then it expands again and is stuck. im going to play with panel apps and restarting and get back to you.

---

### Post by dartakaum on 2007-02-05
same happens here.

---

### Post by elektronaut on 2007-02-06
I switched back to Gnome now. XFCE doesn't seem to be sufficiently supported.

---

### Post by Miaowara on 2007-02-21
I was having that problem too. 

I found the following will reset the panels back to their correctly autohide-ing glory:

```
xfce4-panel -r
```

This problem seems to have cleared up for me now though, so I rarely need to use the command.:-k

---

