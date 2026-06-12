---
title: "Kubuntu: Script at startup doesn't run"
date: 2006-12-18
forum: Desktop Environments
---

### Post by chucknorris on 2006-12-18
Hello, I have a script to set alsamixer PCM volume to a given level.

It's called alsa-pcm.bash and contains:

#!/bin/bash
/usr/bin/amixer -q set PCM 10% unmute

/usr/bin/amixer -q set PCM 90% unmute &

It's set as executable, and is saved to .kde/Autostart. But somehow the levels in alsa are all at 100% at bootup. If i click the script in konqueror it sets the levels correctly.

Any ideas please? Thanks

---

### Post by chucknorris on 2006-12-19
Anyone? ;) Sorry, shameless bump

---

### Post by raul_ on 2006-12-19
I don't know about KDE but isn't there something like a Sessions editor, where you can change your preferences, and set what programs run on startup? At least in gnome that works better than adding the script to the autostart folder.

---

### Post by chucknorris on 2006-12-19
Not that I'm aware of, but thanks anyway :)

---

### Post by raul_ on 2006-12-19
in gnome it's under System-> Preferences -> Sessions. There must be an equivalente in KDE. Sorry i can't be more specific

---

