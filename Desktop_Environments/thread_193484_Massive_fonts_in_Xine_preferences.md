---
title: "Massive fonts in Xine preferences"
date: 2006-06-10
forum: Desktop Environments
---

### Post by Rondonjin on 2006-06-10
Is there any way to change the size of the fonts in the Xine preferences dialogues? They are a tad on the huge side. See attached shot.

Wayne

---

### Post by vdrmrt on 2006-06-20
I have the same problem, i tried a lot of stuf but they had no effect. This problem also causes big and ugly subtitles. It seems that the fonts are just bold.

Anybody any idea?

---

### Post by rai4shu2 on 2006-06-20
It's using the old GTK engine. You can customize that with a few themes available here:

[http://www.gnome-look.org/index.php?page=1](http://www.gnome-look.org/index.php?page=1)

I have no idea how to make the font look much nicer, though.

---

### Post by temcat on 2006-06-20
[QUOTE=rai4shu2]It's using the old GTK engine.[/QUOTE]

It's not even GTK I suppose, more like Motif.

---

### Post by DigitalAxis on 2006-09-06
Rondonjin, at least yours are READABLE.  Mine are so big the text for each option overlaps at least half way over the next option, so tabs, sliders, textboxes, all end up redrawn when I mouse over them.

---

### Post by DigitalAxis on 2006-09-06
Well, according to brief preliminary searching on my part, xine-ui uses the libxft2 library,and xft simply renders fonts for applications...

Further study from Xine themselves suggests the fonts Xine wants to use are HARD-CODED INTO THE PROGRAM (so we'd have to edit and recompile the program to ask for different fonts, or change the helvetica system font they seem to use...)

Reference here:

This appears to be a patch for the source code, enlarging the windows so the text will fit. Lemme say that again: ENLARGING THE WINDOWS SO THE TEXT WILL FIT. Note how the font in question is specified right there...  GRRR...
[http://sourceforge.net/mailarchive/message.php?msg_id=20647489](http://sourceforge.net/mailarchive/message.php?msg_id=20647489)

GXine apparently wasn't configurable until... well, at least after October 2005.  And that's GTK2-based.
[http://sourceforge.net/mailarchive/message.php?msg_id=13310951](http://sourceforge.net/mailarchive/message.php?msg_id=13310951)

Long story short; Xine-ui seems to have been very badly designed, such that international users have had to ask on their mail archives for fonts with sufficient characters to render their languages.  You can create custom On-Screen-Display fonts (configurable in ~/.xine/config) but that's it.

This sucks.

---

### Post by skymt on 2006-09-06
There's good news, though! A workaround!

Use mplayer or vlc.

---

