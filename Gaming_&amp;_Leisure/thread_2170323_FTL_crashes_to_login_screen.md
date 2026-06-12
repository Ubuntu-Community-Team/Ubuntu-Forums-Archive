---
title: "FTL crashes to login screen"
date: 2013-08-25
forum: Gaming &amp; Leisure
---

### Post by heptapod on 2013-08-25
Recently upgraded to 13.04 for Steam and so I can play FTL. Thing is FTL will show the loading screen but once the loading bar is full it'll kick me to the login screen for Ubuntu. I'm using an Acer 5534 if that helps.

---

### Post by heptapod on 2013-08-25
Works now! Just had to do this:

mv $HOME/.local/share/Steam/SteamApps/common/FTL\ Faster\ Than\ Light/data/amd64/lib/libstdc++.so.6 $HOME

---

