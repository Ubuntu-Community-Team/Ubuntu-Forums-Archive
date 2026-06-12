---
title: "Kwin Desktop-Effects now records screencaptures! So how do you play it's .cps file?"
date: 2008-02-06
forum: Desktop Environments
---

### Post by Ubuntiac on 2008-02-06
I need to record a series of screencaptures on KDE4.

Unfortunately the venerable krecordmydesktop works perfectly in KDE 3 and dies instantly on kde4. Desktop effects has an option to record the desktop with Meta-F11, which seems to save the file as kwin_video.cps in the home directory.

Does anyone have the faintest idea of how to then play / convert a .cps file?

---

### Post by uptonm on 2008-04-14
Its a capseo video file, from the captury video recording program. to play the file, enter this in the terminal
cpsrecode -i kwin_video.cps -o - | mplayer -
(according to [http://forums.gentoo.org/viewtopic-p-4453142-highlight-.html?sid=3dc1b7610c65627be4de97f898fff42e](http://forums.gentoo.org/viewtopic-p-4453142-highlight-.html?sid=3dc1b7610c65627be4de97f898fff42e))

I'm not sure, but you might have to install capseo package as well.

sudo apt-get install capseo

good luck, 
 Mike

---

