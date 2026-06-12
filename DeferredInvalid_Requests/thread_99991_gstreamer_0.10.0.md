---
title: "gstreamer 0.10.0?"
date: 2005-12-06
forum: Deferred/Invalid Requests
---

### Post by akurashy on 2005-12-06
was released yesterday!

[http://gstreamer.freedesktop.org/](http://gstreamer.freedesktop.org/)

---

### Post by strikeforce on 2005-12-06
Is it in dapper yet?

[http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by doclivingston on 2005-12-06
Gstreamer 0.10 isn't going to be any use unless you also backport applications that use it. Banshee has partial support in 0.10.0, Totem supports it in cvs, Rhythmbox has a patch that should land in cvs soon. So backporting it probably won't be overly useful at this stage.

---

### Post by ssam on 2005-12-10
its now in dapper and can coexist with 0.8.

i dont think any apps have been rebuilt for it though.

see [http://www.ubuntuforums.org/showthread.php?t=101534](http://www.ubuntuforums.org/showthread.php?t=101534)

---

### Post by picpak on 2005-12-12
[http://www.banditshome.net/downloads.html](http://www.banditshome.net/downloads.html) I've found this; haven't tried it yet though.

---

### Post by jdong on 2005-12-12
gst multiverse and other gstreamer plugins do not seem to be available yet -- let's hold off until everything is together and we see some true benefits in backporting the stack.

---

### Post by elwood_j_blues on 2006-01-06
[QUOTE=jdong]gst multiverse and other gstreamer plugins do not seem to be available yet -- let's hold off until everything is together and we see some true benefits in backporting the stack.[/QUOTE]

Has anything happened meanwhile? The out-of-sync problem in Totem is quite annoying :???:

Also, how about PPC packages? (I run Ubuntu on Mac...)

---

### Post by macleod199 on 2006-01-09
[QUOTE=elwood_j_blues]Has anything happened meanwhile? The out-of-sync problem in Totem is quite annoying :???:

Also, how about PPC packages? (I run Ubuntu on Mac...)[/QUOTE]

There are currently far more problems with video in 0.10 than in 0.8. As in some videos not even loading, some reporting the total time as 0:00, and seeking being completely rebroken. So don't be in a rush to suffer our pain. :)

---

### Post by elwood_j_blues on 2006-01-09
[QUOTE=macleod199]So don't be in a rush to suffer our pain. :)[/QUOTE]

I see - this makes me way more patient, thanks ;)

---

