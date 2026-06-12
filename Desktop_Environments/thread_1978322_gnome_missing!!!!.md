---
title: "gnome missing!!!!"
date: 2012-05-11
forum: Desktop Environments
---

### Post by hamidhqs on 2012-05-11
upgrading to 12.04, I was using gnome without problem; then I used Unity shell but when I wanted to come back to gnome in login window, the gnome didn't open and instead unity opened....

---

### Post by MG&amp;TL on 2012-05-11
Gnome shell (3) or gnome 2?

If the former, try:

```
sudo apt-get install --reinstall gnome-shell
```

If the latter, then you have problems, as gnome 2 is no longer supported. I can list several forks/clones/alternatives if that's the case.

---

### Post by hamidhqs on 2012-05-11
it's gnome 3.2.1 and i did what you said but it didn't work...

---

### Post by MG&amp;TL on 2012-05-11
Okay, just thinking of all the things that could possibly go wrong.

Things to try (note try, I have no idea what's wrong):

1) Can you run Gnome-shell/Unity3d? It's easy to get confused between Unity and Unity2d (fallback), which is what gets launched if your machine can't cope.

2) Let's go for PURGE!

```
sudo apt-get purge gnome-shell
sudo apt-get install gnome-shell
```

3) "Didn't work"? Error, or just no change?

4) Backup and (re)move any themes you've installed. It's possible they're incompatible.

Other than that, I have no clue. You may want to try a fresh install, as these often create less problems. Current GS version is 3.4...?

---

### Post by VanillaMozilla on 2012-05-11
It's called gnome-fallback or Gnome Classic.  Check Synaptic for the packages.  Then select on the login screen.

---

### Post by kansasnoob on 2012-05-12
I'm not sure I'm following you but is any of this helpful:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

---

