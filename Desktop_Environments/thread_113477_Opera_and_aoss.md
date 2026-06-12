---
title: "Opera and aoss"
date: 2006-01-06
forum: Desktop Environments
---

### Post by Third Thoughts on 2006-01-06
My problem has a short version and a long version. The short version is I'm trying to get opera to run its sound through aoss instead of whatever the default is. The long version explains why I'm trying to do this. In firefox I've found that changing the "FIREFOX_DSP" variable in mozilla-firefoxrc from "auto" to "aoss" gives me much better quality sound in flash. Prior to the change it sounded like my speakers were blown out or something. In opera, I have that same bad sound quality. I found an opera configuration file /etc/opera6rc, but can't find any information on how to go about changing the sound wrapper. I've also tried running "aoss opera" instead of just plain opera, but for some strange reason this completely kills flash so it no longer works at all. I've done a search on the Opera forums and googled all sorts of variations on "opera through aoss" or "aoss and opera" but can't seem to find anything. Anybody have some suggestions?

~Andrew S.

---

### Post by pizzach on 2006-01-06
crazy, but try uninstalling esd and see if opera dives for alsa or aoss on it's own.

---

### Post by pizzach on 2006-01-06
note: make sure you don't have any other programs that use alsa open when/if you test opera.  If opera ends up using alsa, it will hog the sound.

---

### Post by Third Thoughts on 2006-01-07
[QUOTE=pizzach]crazy, but try uninstalling esd and see if opera dives for alsa or aoss on it's own.[/QUOTE]

I didn't uninstall esd, but I did do "killall esd" and it didn't seem to change much. In fact I'm almost positive I'm not using esd, because I think I made alsa my default when I installed my second sound card. The Gnome volume control tool is using an alsa mixer, so I'm pretty sure about that fact. I'm reluctant to actually uninstall esd though, because it seems to be a dependency for a bunch of stuff.

~Andrew S.

---

