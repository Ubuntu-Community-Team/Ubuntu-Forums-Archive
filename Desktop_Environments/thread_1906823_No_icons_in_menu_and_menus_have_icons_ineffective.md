---
title: "No icons in menu and menus_have_icons ineffective"
date: 2012-01-10
forum: Desktop Environments
---

### Post by Mhz42 on 2012-01-10
All my gtk apps (Firefox, gnome, gimp, eclipse, etc.) do not have menu icons on a fresh ocelot install. I had the same the problem one year ago, but managed to resolve it.

The classical workaround to this issue is to set the following gconf property:
gconftool-2 --type boolean --set /desktop/gnome/interface/menus_have_icons true

(and optionally buttons_have_icons as well)

Except that this time, it doesn't work... I tried everything, reset my account, created a new one, each time resettings these boolean values...The icons won't show up.

Does anyone have an idea of what going wrong? Should I submit a bug report?
Thanks,
Marc

---

### Post by mcduck on 2012-01-10
No need for a bug report, it's just that 11.10 has already moved from gconf to gSettings/dconf...

Install the [dconf-tools]("apt:dconf-tools") -package, then start *dconf-editor* and you'll find the releavant options under org.gnome.desktop.interface.

...or use the following commands:
```

gsettings set org.gnome.desktop.interface menus-have-icons true
gsettings set org.gnome.desktop.interface buttons-have-icons true
```

---

### Post by Mhz42 on 2012-01-10
> **mcduck said:**
> No need for a bug report, it's just that 11.10 has already moved from gconf to gSettings/dconf...

Install the [dconf-tools]("apt:dconf-tools") -package, then start *dconf-editor* and you'll find the releavant options under org.gnome.desktop.interface.

...or use the following commands:
```

gsettings set org.gnome.desktop.interface menus-have-icons true
gsettings set org.gnome.desktop.interface buttons-have-icons true
```

Thanks-a-lot :)  It worked perfectly.

It's the first time I hear about dconf... Glad to learn something new :D

Marc

---

