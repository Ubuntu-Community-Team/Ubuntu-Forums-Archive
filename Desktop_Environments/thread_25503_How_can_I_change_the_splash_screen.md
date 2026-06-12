---
title: "How can I change the splash screen?"
date: 2005-04-10
forum: Desktop Environments
---

### Post by titus on 2005-04-10
hi how can i change the login progress splash screen, and the desktop colour as gnome is logging in?

I don't really like brown you see.

:)

---

### Post by soul_rebel on 2005-04-10
background color is a gdm option. sudo gdmsetup
for splash:
go to /usr/share/pixmaps/splash/
and change the ubuntu-splash.png symlink to a splash you like

bye

---

### Post by carlc on 2005-04-10
If you change the splash, you might also want to change the desktop color under desktop background properties as well as the login in screen's background color (system > administration >  login screen setup > standard greater tab > background color).  :wink:

---

### Post by soul_rebel on 2005-04-10
> login in screen's background color (system > administration > login screen setup > standard greater tab > background color). 

that's the same of doing "sudo gdmsetup"

---

### Post by carlc on 2005-04-10
My bad. I did not fully read your post. I thought you just addressed the slash screen.

---

