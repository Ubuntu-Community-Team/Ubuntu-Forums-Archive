---
title: "Size of interface"
date: 2005-10-13
forum: Desktop Environments
---

### Post by gaz514 on 2005-10-13
When I run Ubuntu on my own PC, everything looks big, if you know what I mean, like, the fonts in particular, as well as Emacs windows which are absolutely massive. I use a resolution of 1280*1024. I thought this might just be a Linux issue, but at my uni when I use their Linux computers (Fedora Core 3), everything on the screen is a nice size (fonts definitely look smaller, and Emacs windows are a reasonable size). I looked at all the settings and they have exactly the same resolution, font size, font DPI, etc.... so does anyone know why stuff on Ubuntu looks so big? Is it a setting somewhere that I missed?

---

### Post by nutshell on 2005-10-13
Are you sure you are actually have a 1280x1024 resolution ? (take a screenshot of the desktop and check resolution in GIMP)

---

### Post by gaz514 on 2005-10-13
I checked, yes I do have a 1280x1024 resolution.

---

### Post by zeroverse on 2005-10-13
Can you post your screenshot here so we can see exactly what you mean?

Thanks.

---

### Post by ubuntumaneh on 2005-10-13
What comes to emacs, I can suggest you to edit the .Xresources. Just an example:

!My Xresources 
!

xterm*background: Black
xterm*foreground: PaleGoldenrod
xterm*cursorColor: ivory2
xterm*font: 10x20
!xterm*geometry: 75x25

emacs*background: Black
emacs*foreground: PaleGoldenrod
emacs*cursorColor: White
emacs*pointerColor: yellow
emacs.font: 10x20
emacs*geometry: 100x35
------------------------------------------
After the chages you have to restart X.

Play with the numbers of geometry and font. As come with font you can look at google for names of fonts (10x20 is very good for me in the university computer, but at home is awful, so I change for 7x13).

See if this solves. But I suggest you post a screenshot.

---

