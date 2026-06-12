---
title: "NX --  fonts and  colors"
date: 2007-07-08
forum: Desktop Environments
---

### Post by parsival on 2007-07-08
Hi list,

I am having problems with colors and fonts using nx

1) emacs can't find the color black
2) R (a stats language) can find fonts
	"X11 font at size 14 could not be loaded"

I searched the nx packages for strings "rgb" and "font"

% strings /usr/lib/nx/nxagent | grep /rgb
/usr/X11R6/lib/X11/rgb
% strings /usr/lib/nx/nxagent | grep font
/usr/X11R6/lib/X11/fonts/misc/,/usr/X11R6/lib/X11/fonts/Speedo/,
/usr/X11R6/lib/X11/fonts/Type1/,/usr/X11R6/lib/X11/fonts/75dpi/,/usr/X11R6/lib/X11/fonts/100dpi/,/usr/X11R6/lib/X11/fonts/TTF/


and them made some links

% cd /usr/X11R6/lib/X11/
% ls -l
total 4
lrwxrwxrwx 1 root root   20 2007-07-05 12:00 fonts -> /usr/share/X11/fonts/
drwxr-xr-x 3 root root 4096 2006-03-10 02:45 icons/
lrwxrwxrwx 1 root root   25 2007-07-04 15:00 locale -> ../../../share/X11/locale/
lrwxrwxrwx 1 root root   16 2007-07-05 08:48 rgb -> /etc/X11/rgb.txt
lrwxrwxrwx 1 root root   16 2007-07-05 08:42 rgb.txt -> /etc/X11/rgb.txt
lrwxrwxrwx 1 root root   12 2006-03-10 02:43 xkb -> /etc/X11/xkb/

This fixed the color problem but not the font problem. Any ideas?

Also does this look right (below)? Is the "freenx application" part of nx or something 
else? Can I remove it?


dpkg -l \*nx\*
freenx   0.4.4+0.4.5-3ubuntu2     The FreeNX application/thin-client server
nxagent  1.4.92+1.5.0-4ubuntu0    NoMachine NX - nesting X server with 
nxlibs                   1.4.92+1.5.0-4ubuntu0    NoMachine NX - common agent 
nxviewer                 1.4.92+1.5.0-4ubuntu0    NoMachine NX - nesting X 

Bye
Parsival

---

