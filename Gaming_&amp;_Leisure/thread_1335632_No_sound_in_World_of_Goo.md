---
title: "No sound in World of Goo"
date: 2009-11-23
forum: Gaming &amp; Leisure
---

### Post by Saronn on 2009-11-23
I have Ubuntu 9.10, and there isn't any sound in World of Goo. This happens with a lot of games, actually. But I want World of Goo to work the most. I had to delete Pulseaudio when I got 9.10, because with it, I didn't have any sound at all. So, what can I do to make it work?

---

### Post by ajgreeny on 2009-11-23
I suspect you should really rinstall pulse and everything you removed for that, then try to get sound working again.  I found that sound was a bit dubious in 9.10 until I ran alsamixer and raised and unmuted several of the audio channels showing in that.  It's a terminal application with a simple gui that is navigated with cursor keys and the M key to unmute/mute channels.

Give that another try if you can and see if it is any better.  Pulse seems to be an absolute necessity for karmic to manage sound properly.

If you really don't want to try that or can't remember what you removed try running alsamixer with what you now have, and see if anything that is needed is muted or too low.

---

### Post by Saronn on 2009-11-23
Under GNOME Alsa mixer, everything is maxed except Master. I have a thread on when I didn't have sound, and I tried everything until finally someone said to delete Pulseaudio. I really don't think that reinstalling Pulseaudio will help me here.

---

### Post by Vadi on 2009-11-23
Re-install pulseaudio (because uninstalling it obviously failed to help), install the "pavucontrol" tool, make sure that stuff isn't muted / proper stuff is playing the sound.

---

