---
title: "crash during &quot;upgrade&quot; to heron: lost icons and buggy desktop"
date: 2008-03-08
forum: Desktop Environments
---

### Post by keratos on 2008-03-08
I performed an upgrade to Heron 8.04 but during the upgrade I inadvertently logged out, well I actually did a Ctrl-Alt-Backspace to stop a crashed app.

Upon trying to log in I got all sorts of errors and the GUI eventually died. I couldnt log in.

Eventually managed to get an Xterm and using sudo, did the following

```

dpkg --configure -a
apt-get update
apt-get dist-upgrade

```
Now most stuff is working but a few things are buggy:
1. I cannot click on image and "set as desktop background".  The button just doesnt set the background
2. f I install and select a new icon set, the folder icons stay as the default "Gnome" iconset. Other icons do however get changed.
3. Some themes work, some dont.
4.Some strange errors at boot time.

Is there a way to "clean" or "repair" the system other than what I've done?

---

