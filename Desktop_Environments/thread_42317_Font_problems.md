---
title: "Font problems"
date: 2005-06-17
forum: Desktop Environments
---

### Post by b222b on 2005-06-17
After installing some additional fonts in Ubuntu (gsfonts-x11 and msttcorefonts), I found that font in some applications, which I believe use GTK+ based menus, such MPlayer, XMMS, or XCDRoast, is extremely small, almost illegible. I tried to uninstall these new fonts. However, after unistalling gsfonts-x11, some applications stopped working  at all, so I had to reinstall them again.

Anyway, my question is: 

Does anyone know how I can select or resize fonts in the above mentioned applications, given that font preferences in Gnome Control Centre do not appear to affect them at all?

---

### Post by skoal on 2005-06-17
XMMS and Mplayer still use GTK-1.x I believe.  In that case, you'll need to create a '~/.gtkrc' file with a specific font/size you want.  I used to have my own custom '.gtkrc' lying around somewhere but use all gtk2 apps now.  There may be another way to do it, but I'm not aware of it.

\\//_

---

### Post by b222b on 2005-06-17
I did try to add a .gtkrc file in my home directory with "gtk-font-name = (here I added different fonts and different font sizes)" in the file, but it did not seem to affect the font in these applications. Not sure what to do...

---

### Post by b222b on 2005-06-17
Well, I just found that the file in the home directory should be called .gtkrc.mine and should contain something like this to work:
--------------------------------------------------------------------
style "default-text" {
       fontset = "-adobe-helvetica-normal-r-normal-*-12-*-*-*-*-*-*
}

class "GtkWidget" style "default-text"
-----------------------------------------------------------------

well, it worked... :-)

---

### Post by jarrett.wold on 2005-06-18
I avoided all that by Installing: (All available via your favorite apt-get mechanism)

Beep Media Player (XMMS fork w/ GTK2 support) 
Gnome Baker
Totem (xine backend)*

*Gstreamer ran sluggish for me.  Rather than digging for hours, I just switched the backend to xine.  Quite happy since.

---

