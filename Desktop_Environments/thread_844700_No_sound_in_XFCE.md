---
title: "No sound in XFCE"
date: 2008-06-29
forum: Desktop Environments
---

### Post by FFighter on 2008-06-29
Hello folks,

I'm running Ubuntu 8.04 and just started to try XFCE and I'm really liking it. However, there's a major problem I've found: Sound playback is not working. I just tested it again in Gnome and it works fine, but when I log back into the XFCE session, there's no sound.

I've tried to run alsamixer in the terminal to see if I would get any useful output. Here's what I've got:

> 
*** PULSEAUDIO: Unable to connect: Connection refused

alsamixer: function snd_ctl_open failed for default: Connection refused


Again, sound works perfectly when I'm using Gnome.

Does anyone know why this is happening?

Cheers,

Marcelo.

---

### Post by j1mc on 2008-06-30
Hi there, FFighter.  Have you tried putting the volume controller plugin into the panel, and adjusting the volume from there?  The volume control applet isn't installed in the top panel by default in xfce/xubuntu, so you may want to give that a try.  Best of luck to you!

---

