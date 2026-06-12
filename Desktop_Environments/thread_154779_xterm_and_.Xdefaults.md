---
title: "xterm and .Xdefaults"
date: 2006-04-03
forum: Desktop Environments
---

### Post by xeen on 2006-04-03
Hi,

I'm trying to write my .Xdefaults file so that it will have the same settings as the command

xterm -bg black -fg white -ls -j -s -sl 10000 +sb -fa DejaVu-Sans-11 -fs 11

My .Xdefaults is currently:

xterm*scrollBar:                    false
xterm*vt100.scrollBar:          false
xterm*vt100.font:                 DejaVu-Sans-11
xterm*background:               black
xterm*foreground:                white
xterm*multiScroll:                 on
xterm*jumpScroll:                 on
xterm*SaveLines:                10000

But xterm do not use this font when starting xterm with this .Xdefaults setting.

When I start xterm via this command with all the flags above it looks as I want.

Can you help me "translate" the xterm -bg [...] line into an working .Xdefaults?
Thanks!

---

### Post by vloris on 2006-04-05
Does it apply any of the settings in your .Xdefaults file or none at all?
You need to reload it into the X resource database after you edited that file by entering in a terminal:
```
xrdb -merge Xdefaults
```
That, or restart your session by logging out and back in again. Btw, I have my resources file called .Xresources, that works but I believe .Xdefaults should be fine too.

---

### Post by xeen on 2006-04-06
[QUOTE=vloris]Does it apply any of the settings in your .Xdefaults file or none at all? [/QUOTE]

Thanks for your help.
It applys everything except the font setting. 

It can be that I should write the full name of the font instead just DejaVu-Sans-11, how can I find it?

---

### Post by kabus on 2006-04-06
Use the xlsfonts or xfontsel utilities to get the full name of the font you want.

---

### Post by xeen on 2006-04-16
Thanks

---

