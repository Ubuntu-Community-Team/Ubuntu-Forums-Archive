---
title: "gnome-shell button placement (want them on the left)"
date: 2010-10-10
forum: Desktop Environments
---

### Post by wheredidrealitygo on 2010-10-10
Hi all.. been a while since I posted actually needing some help, hoping someone can shed some insight onto a problem I'm having.

Fresh install of 10.10, x86_64, installed gnome-shell 

```
sudo apt-get install gnome3-session
```

Can't seem to get the button placement to go on the left like in metacity on the normal gnome session.

using gconf-editor to set "/desktop/gnome/shell/windows/button_layout" to "close,minimize,maximize:"

just doesn't seem to be working. 

any thoughts?

---

### Post by wheredidrealitygo on 2010-10-13
*Edit* - fixed it, my own stupidity, i was using gconf-editor as root (with sudo), didn't realize that to affect the regular account i had to issue gconf-editor without sudo.

changing /desktop/gnome/shell/windows/button_layout" to "close,minimize,maximize:" without issuing sudo to gconf-editor fixed it.

---

