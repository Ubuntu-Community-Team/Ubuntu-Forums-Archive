---
title: "xfce trouble after startx"
date: 2006-02-20
forum: Desktop Environments
---

### Post by stepore on 2006-02-20
on my laptop -- if i use kdm, xfce (xfce4) starts up nice. it's totally 
GUI-windowy and pretty, there's a mouse flashing for the splash screen, 
all comes up great. if i kill X and go to a shell and do 'startx', 
something starts but then fails. it only shows a black screen and  a 
mouse. can't left or right-click on (black) desktop, no menu nothing. i 
have to kill X again.

no error is .xsession-errors and /var/log/Xorg.0.log only shows font 
errors until the kill X message:
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0

not sure if it's font related. but one other thing. on another PC if i 
use xfce4 through kdm, i get that slick GUI with the splash screen just 
like on the laptop, but if i kill X and then startx from a prompt i get 
a *way* different xfce with a really old-school-looking desktop. 
everything is square and plain, you left-clik (not right-click) on the 
desktop and a xfce menu comes on the desktop. nothing fancy, and i 
actually love it. how do i get this plain version of xfce, rather than 
the fancy-gui xfce on my laptop?

using ubuntu breezy (5.10).

---

### Post by syklitengutt on 2006-02-21
try theese commands.
xfdesktop
xfce4-panel

---

### Post by stepore on 2006-02-22
[QUOTE=syklitengutt]try theese commands.
xfdesktop
xfce4-panel[/QUOTE]
thanks for the reply.

don't forget i'm on a command line, no X running. with those commands i get:
(xfdesktop:21591): Gtk-WARNING **: cannot open display:

i found the 'startxfce4' command, and it does work, but it brings up the slicker xfce4 desktop.

Whether or not i get this working, does anyone know what i'm talking about with the plain xfce desktop? what is that? i don't mind the slicker xfce desktop, but it still does use quite a bit of resources and RAM. so, what is this old-school plain desktop, where can i get that and how can i get it working properly?

thanks again.

---

