---
title: "questions about gconftool-2 syntax"
date: 2007-11-16
forum: Desktop Environments
---

### Post by Zelut on 2007-11-16
I'm trying to script just a few desktop settings via gconftool-2.  I'm wondering if anyone can give me some suggestions on syntax.  Here is what I would like to change:

I need to set the default sound mixer.  Normally done via the GUI with:
system > preferences > sound : "default mixer tracks : device"

the gconf path to this setting as far as I can tell is:
> /desktop/gnome/sound/default_mixer_tracks

and this needs to be set to PCM

I also think I may need to change the value here to the same:
/apps/panel/applets/mixer_screen0/prefs/active-track

If someone can help me with the right syntax to set these via gconftool-2 I would appreciate it.  I need to script this.  Thanks.

---

