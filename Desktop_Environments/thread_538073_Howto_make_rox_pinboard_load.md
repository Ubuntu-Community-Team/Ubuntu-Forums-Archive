---
title: "Howto make rox pinboard load"
date: 2007-08-29
forum: Desktop Environments
---

### Post by DavidMaas on 2007-08-29
I installed Xubuntu + ROX + JWM + XDM
In the jwm terminal i can type rox -p=blabla... and i have a pinboard

When i log out and log in again the pinboard is gone and i have to load it again. How can i make this autoload at startup?

---

### Post by oswaldkelso on 2007-09-28
[http://joewing.net/programs/jwm/config.shtml](http://joewing.net/programs/jwm/config.shtml)

you could edit your .jwmrc then its just one click? on my system i had to copy the jwmrc from /etc/jwm/jwmrc to my home folder

jwm is really faston low end systems

---

### Post by kerry_s on 2007-09-28
if your going to be switching between desktops use the .jwmrc, you'll see a section for startup app's. if your just going to use jwm you can use a .xinitrc.

mousepad ~/.xinitrc

feh "eval `cat $HOME/.fehbg`" &
rox -p=icons &

jwm


put jwm at the bottom to start the desktop. i recommend feh for the background, as xli, just sucked.

---

