---
title: "Gnome/GTK (?) Issues"
date: 2006-04-11
forum: Desktop Environments
---

### Post by Selbstmord on 2006-04-11
I have attached a sample picture of the VLC Media Player here, showing my problem, well, it's not hindering me in some way, it's just that I would like VLC (and other applications) to match the Gnome theme, and the fonts are hideously large, causing all sorts of trouble (working fast in Audacity is a no-no), I get the same problem in Fluxbox/KDE/Gnome/XFCE, so it doesn't appear to be something Gnome related (or does it?), also, my installation came like this out of the box.

What's the problem, and how do I fix it?

[IMG]http://i3.photobucket.com/albums/y53/selbstmord/c7870883.jpg[/IMG]

---

### Post by issueperson on 2006-04-11
have you tried adjusting:
applications > system > preferences > font
?

issueperson

---

### Post by Selbstmord on 2006-04-12
Durr... As you probably can see, it's not only the fonts that are "wrong", the color scheme is too. And I tried System > Preferences > Font - still a no-go.

---

### Post by art on 2006-04-12
I think VLC uses GTK1, and instead GNOME is using GTK2, so that's why you have the mismatch. To beautify this a little bit try:
[http://ubuntuforums.org/showthread.php?t=107135&highlight=gtk1](http://ubuntuforums.org/showthread.php?t=107135&highlight=gtk1)
Makes it look a bit better...

---

### Post by Selbstmord on 2006-04-12
But it's not only VLC... Many other apps have it, too, but as you suggested, it may be the GTK1 thing, I'll have to investigate...

---

### Post by Selbstmord on 2006-04-12
I installed Ubuntu on another laptop, and didn't get this problem, what the hell is going on?

---

### Post by art on 2006-04-12
what other apps have the same issue?

---

### Post by Selbstmord on 2006-04-12
VLC, Cedega, GXine, MPlayer, Audacity, XMMS pretty much everything except Firefox, Synaptic and OpenOffice...

---

### Post by art on 2006-04-12
I don't have Cedega, Audacity, but VLC, Mplayer, xmms ARE using GTK1. Gxine is not though, but xine I think does. So your list seems to be on GTK1 side... What about evince, gqview, gedit, gcalctool? These are supposed to be GTK2.

---

### Post by Selbstmord on 2006-04-13
Gedit galctool, gqview and evince look "normal"...

Oh, and you were right, Gxine looks ok, Xine looks like shit. Also, Totem looks okay too.

---

