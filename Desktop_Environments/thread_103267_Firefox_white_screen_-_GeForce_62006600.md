---
title: "Firefox white screen - GeForce 6200/6600"
date: 2005-12-13
forum: Desktop Environments
---

### Post by kjkrum on 2005-12-13
A few weeks ago, somebody in another Ubuntu community started having a weird problem where Firefox would start rendering pages as mostly white, with just a few controls or images drawn.  He posted a good screenshot here: [http://www.livejournal.com/community/ubuntu_users/41832.html?view=407656](http://www.livejournal.com/community/ubuntu_users/41832.html?view=407656)

I thought nothing of it until the exact same thing started happening to me.  In my case, this "white screen of death" spreads to other windows, until soon GNOME is entirely locked up and even ctrl-alt-backspace doesn't work.  Yet I can still move my mouse pointer around.  Also, whenever I move my text cursor using the arrow keys, it leaves trails of itself between characters.

All this started when I upgraded my GeForce4 MX440 to a GeForce 6200.  Curiously, the other guy has a GeForce 6600.

Has anyone else seen this?

---

### Post by RAOF on 2005-12-13
Yup.  I had this problem, with a 6600GT.  The solution I found was to install the nvidia-glx drivers.  They work better with the new cards than the open-source nv drivers.

---

