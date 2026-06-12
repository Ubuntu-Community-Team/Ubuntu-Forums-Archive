---
title: "mp3 support?-???"
date: 2006-01-17
forum: General Help
---

### Post by open_coder on 2006-01-17
I just installed Ubuntu 5.10. I need to get mp3 support for the gstreamer plugin. Or use another plugin with amarok. Can someone explain how to do this?

--Alex

---

### Post by o_fortuna on 2006-01-17
[QUOTE=open_coder]I just installed Ubuntu 5.10. I need to get mp3 support for the gstreamer plugin. Or use another plugin with amarok. Can someone explain how to do this?

--Alex[/QUOTE]
Simply open up Synaptic (System-->Administration-->Synaptic Package Manager) and search for gstreamer0.8-mad. Alternatively, open up a terminal (Applications-->Accessories-->Terminal) and type
```
sudo apt-get install  gstreamer0.8-mad
```This will enable mp3 support in gstreamer players (Totem, amaroK, ect.)

---

### Post by MJSOnline on 2006-01-17
Or install Automatix [http://ubuntuforums.org/showthread.php?t=66563]("http://ubuntuforums.org/showthread.php?t=66563") it does it all for you.

Matthew

---

### Post by open_coder on 2006-01-17
it works. it works!!!. thanks guys.

--alex

---

