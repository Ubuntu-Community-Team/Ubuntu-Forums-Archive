---
title: "Game trouble in 10.04"
date: 2010-05-28
forum: Gaming &amp; Leisure
---

### Post by lukeiscool on 2010-05-28
Hey Guys.

Just installed ubuntu 10.04 and I am having some trouble running games. I had these games in 8.04 and they worked fine. Now they are really laggy. Is there anything i need to install to make them run properly?

Cheers

Sir Luke

---

### Post by Cresho on 2010-05-28
ya from from my expirience, uninstalled pulseaudio completely.  then I went directly to kubuntu since pulseaudio is weak in that os.  you need to disable pulseaudio

gedit ~/.pulse/client.conf
and add "autospawn = no" without quotes

then create a script at launchh or under sessions startup

pulseaudio -k

or
killall pulseaudio

if this dont work

sudo apt-get remove pulseaudio

your desktop will have no sound like window effect and such but you will have flash video, audigy and music player working fine under alsa.  just gnome desktop related to pulseaudio wont work after this.  but you free up everything after for gameplay and everything else you want to do.

---

