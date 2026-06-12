---
title: "Strange icons in Unity"
date: 2017-09-29
forum: Desktop Environments
---

### Post by jeremy31 on 2017-09-29
I have had this happen before but I don't remember what I did to fix it or where these icons come from.  Any ideas?  They showed up after my last updates

---

### Post by Frogs Hair on 2017-09-29
The location is usr/share/icons and are selected in appearance settings. I've only seen branding/artwork updates in the development version.  The brown folders belong to the gnome icon set on Artful . I'd try changing sets and logging out and in.

Edit you can also try the following.

Restore Defaults:```
unity --reset-icons
```

```
sudo apt-get install dconf-tools
```

```
dconf reset -f /org/compiz/
```

If Needed: ```
setsid unity
```

---

### Post by jeremy31 on 2017-09-30
The commands worked until a reboot and then they changed until I logged out and back in but I think I found the cause- some of the hidden folders in /home where owned by root and things are normal after changing the owner

Thanks for the help

---

