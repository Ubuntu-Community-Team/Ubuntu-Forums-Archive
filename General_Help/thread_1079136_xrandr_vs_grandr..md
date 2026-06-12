---
title: "xrandr vs grandr."
date: 2009-02-24
forum: General Help
---

### Post by alfonz19 on 2009-02-24
Hi,

I'm experiencing some problems, but maybe it's not a problem, maybe I just not understand it.

So what's "wrong":
I have work notebook, which has almost dead lcd display, but I use it only at work where I also have good lcd monitor. After boot, both monitors are on, cloning. After I log in, monitor on vga turns off while lcd panel on lvds remains on. When I use grandr, I can swith this state - I do not want wider screen neither cloning - that lcd display is not usable. So I turn lvds off and vga on. That will succeed, but my kde environment still behaves like the vga has screen resolution of lvds (maximized windows are not wide as monitor). Does anyone know what to do with that?

moreover I've tried to create some script, since everyday need to use grandr is tedious. I've tried following commands, but although grandr works, these do not:

xrandr --output VGA --auto --output LVDS --off
xrandr --output VGA --mode 1680x1050 --pos 0x0 --same-as LVDS

can anybody suggest me, what to do?
thanks in advance
alfonz.

---

