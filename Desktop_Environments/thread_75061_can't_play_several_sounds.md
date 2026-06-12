---
title: "can't play several sounds"
date: 2005-10-13
forum: Desktop Environments
---

### Post by mangar on 2005-10-13
Breezy seems to be still broken in the sound department.
my integrated sound device
analog devices AD1981B 
isn't supported by ALSA, therefore I'm using OSS.
when playing music with amarok, I can't make a call in skype.
when using firefox, I can't play a movie in totem.
etc.

I've using gnome, and got esd disabled.
how can I solve this mess?

---

### Post by karuptdata on 2005-10-13
have you tried this post it resolved my issue with multiple sounds! try it [http://ubuntuforums.org/showthread.php?t=32063&highlight=multiple+sounds]("http://ubuntuforums.org/showthread.php?t=32063&highlight=multiple+sounds")

---

### Post by mangar on 2005-10-13
It doesn't work.
skype reports that /dev/dsp is blocked.

(and I'm forced to close amarok in order to use it)
I do manage now to run mplayer + amarok.

---

### Post by Wolki on 2005-10-13
[QUOTE=mangar]I've using gnome, and got esd disabled.
how can I solve this mess?[/QUOTE]

Enable esd, that's what it's for. :)

No, your problem might not be 100% solvable - some apps don't play nice with esd. If a program doesn't support esd, you will not be able to have multiple sounds while that app accesses the sound card. The annoying esd freeze bug of Hoary seems to be gone though, that's a very good thing. If an app is not compatible with esd it doesn't crash that app anymore if it tries to access the soundcard, it gets the exclusive rights to it instead.

(you could also try arts, but i personally have not had good success with that...)

---

