---
title: "minimize maximize buttons missing from certain application windows in gnome"
date: 2015-11-17
forum: Desktop Environments
---

### Post by miatawnt2b on 2015-11-17
I just upgraded from 15.04 to 15.10. Afterward, I noticed that my minimize/maximize buttons were missing from the title bar on most applications. for instance, pidgin, libreoffice and firefox do not have the buttons, but tweak tool does.

sudo gsettings set org.gnome.desktop.wm.preferences appmenu ':minimize,maximize,close' returns an error No such key 'appmenu'

I'm stuck.

---

### Post by sammiev on 2015-11-17
Hi miatawnt2b,

Select "Tweak Tools" -> "Windows" -> Go down to "Titlebar Buttons" and turn then on.

---

### Post by miatawnt2b on 2015-11-17
Yes, Both are already on, and turning them off will disable the buttons on tweak-tool's window. no changes to Firefox/pidgin/libre/etc.

---

### Post by mc4man on 2015-11-17
While likely not related to current issue you should keep in mind that running gsettings as root configures settings for root, not you. 
So you should stop doing that unless you want to alter root's config...

---

