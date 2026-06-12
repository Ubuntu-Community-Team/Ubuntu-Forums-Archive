---
title: "Pidgin 2.5.5"
date: 2009-03-03
forum: General Help
---

### Post by fearful on 2009-03-03
I'm getting an error when installing pidgin 2.5.5. I completely removed the 2.5.2 version with purge and install pidgin-data2.5.5 and when I go on installing pidgin2.5.5 I get a dependency error with libgtk2.0-0, and I checked and I have it installed already to the newest version any ideas? 

Thanks!

---

### Post by Tibuda on 2009-03-03
If you are trying to install it from source, you probably need libgtk2.0-0-dev too. If you are trying to install from GetDeb packages, there's a order you have to follow: pidgin-data, libpurple0, libpurple-bin and pidgin. Then reinstall your Pidgin plugins.

---

