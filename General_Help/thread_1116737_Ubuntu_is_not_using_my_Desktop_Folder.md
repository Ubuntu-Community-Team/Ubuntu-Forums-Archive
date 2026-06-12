---
title: "Ubuntu is not using my Desktop Folder"
date: 2009-04-05
forum: General Help
---

### Post by Jesterday on 2009-04-05
When I installed Jaunty I retained some settings from an old install, but somewhere during the install my Desktop got linked to "/home/darren" instead of "/home/darren/Desktop"

is there anyway to set it up to link my Desktop to /home/darren/Desktop without a reinstall?

I would think there is a setting somewhere allowing me to do this, but I can't find it.

---

### Post by steeleyuk on 2009-04-05
Press <ALT>F2 and type gconf-editor.

Follow the path to /apps/nautilus/preferences/desktop_is_home_dir and uncheck.

---

### Post by Jesterday on 2009-04-05
Thanks for the quick response, but that is already unchecked.

I will try to further clarify my problem. 

Everything I put into the "/home/darren" shows up on my desktop. I need that changed so it doesn't. and so that gnome uses the "/home/darren/Desktop" folder as my Desktop instead.

---

### Post by Jesterday on 2009-04-07
Any other suggestions? Anyone? Bueller? Anyone?

---

