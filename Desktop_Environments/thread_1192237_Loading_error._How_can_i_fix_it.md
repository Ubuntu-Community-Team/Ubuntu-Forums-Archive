---
title: "Loading error. How can i fix it?"
date: 2009-06-19
forum: Desktop Environments
---

### Post by wizzim on 2009-06-19
When I load ubuntu it just goes to the default background and nothing else shows up. The panels are missing. I know this is the result of trying to fix a "644 permissions with .dmrc" I can happily report i fixed the issue with the .dmrc, but as I stated before nothing shows up when i start up ubuntu. I also know how to get into console and xterm, which was used for these codes.

Things I have tried...
```
gconftool-2 --recursive-unset /apps/panel
...
sudo /etc/init.d/gdm [COLOR="Red"]stop[/COLOR]
sudo /etc/init.d/gdm [COLOR="Red"]restart[/COLOR] or sudo /etc/init.d/gdm [COLOR="Red"]start[/COLOR]
```


What do i do from here?
Thanks!
Wizzim

---

### Post by gettinoriginal on 2009-07-13
I have not had to do this in awhile, but try: Reboot, at the sign in screen > options > session > gnome > change session(?) then sign in as usual.  Hope it helps  :p

---

