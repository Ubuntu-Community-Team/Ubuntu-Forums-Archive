---
title: "totem and esd conflicts"
date: 2005-08-05
forum: Desktop Environments
---

### Post by lomomo on 2005-08-05
hi all,
i've problems with totem and esd. Totem seems to work perfect and i can play mp3, ogg and other audio and video files without problems, but it does only work when the esd is not enabled, so rythmbox can't work and i can't enable gnome sound events.

When i enable esd rythmbox and gnome audio events works without problems but totem does not work. If i want to use totem again i need to kill esd, then it starts working again.

So there's a conflict betwen totem and esd and i don't know how to solve it.

---

### Post by heimo on 2005-08-05
[QUOTE=lomomo]So there's a conflict betwen totem and esd and i don't know how to solve it.[/QUOTE]

Just a weak guess... (others will give better advice) If you're using totem-gstreamer (default), try installing totem-xine and retry.

EDIT: Hey! You're new here, welcome!

---

### Post by lomomo on 2005-08-05
Yeah, i'm new here and that was my first post, anyway, i've been using ubuntu since its release. Thanks for your welcome.

About my problems with totem and esd, i'm using totem-xine, ¿should i try to install totem-gstreamer? i don't know what the difference is.

---

### Post by heimo on 2005-08-05
[QUOTE=lomomo]Yeah, i'm new here and that was my first post, anyway, i've been using ubuntu since its release. Thanks for your welcome.

About my problems with totem and esd, i'm using totem-xine, ¿should i try to install totem-gstreamer? i don't know what the difference is.[/QUOTE]

Difference is audio/video framework - "engine" or "backend". But I'm not sure if it has effect in this case. Worth trying, though.

---

### Post by lomomo on 2005-08-05
i installet totem-gstreamer and it now works. Totem visualizations when listening music seems to be slower.

I'll check if im able to open the same audio and video formats and the problem is solved  :)

---

### Post by heimo on 2005-08-05
[QUOTE=lomomo]i installet totem-gstreamer and it now works. Totem visualizations when listening music seems to be slower.

I'll check if im able to open the same audio and video formats and the problem is solved  :)[/QUOTE]

Hmm.. that's interesting. Let's hope it works well, as what I've noticed is that people mostly jump from gstreamer to xine. Gstreamer is newer and should be better (at least in future), but it's known to handle worse some broken video formats (or rather: xine handles bad files gracefully)

---

### Post by lomomo on 2005-08-06
well, i can't play all videos now and totem is crashing a lot.

gnome-vide-thumbnailer is crashing too, it starts consuming a lot of memory and ends freezing the system.

i was not having these problems with videos when using totem-xine, so, is it possible to have totme-xine and esd working without conflicts? i'm the only one having this crashes with totem-gstreamer?

---

