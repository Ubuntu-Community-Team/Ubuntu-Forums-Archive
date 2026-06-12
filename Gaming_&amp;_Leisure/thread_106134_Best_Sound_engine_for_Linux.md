---
title: "Best Sound engine for Linux?"
date: 2005-12-19
forum: Gaming &amp; Leisure
---

### Post by Prudentissimus on 2005-12-19
Hello!


         How are ALSA, ESD, ESS, and other Linux sound "engines" different?

         Which one is the best for 5.1 Audigy 2 sound??? (music, game, both)?

---

### Post by jpkotta on 2005-12-20
I don't know what ESS is, a google seach implied that it's some kind of hardware.  Here is what I do know:

ALSA and OSS are low level (i.e. in the kernel) audio code.  ALSA is newer and as far as I can tell better than OSS.  In a graphics analogy, ALSA and OSS are like the X server.

ESD, ARTS, and JACK are sound servers.  They take sound from several sources, mix it to a single stream, and send it to ALSA/OSS.  The hardware can only play one sound at a time (nevermind 5.1 and all that), so this is necessary if you want to play music and still hear notifications, etc.  JACK seems like the best in theory, it's designed for professional recording, but in practice, most apps don't have output plugins for it.  In my experience, ESD has worked well, but I've had trouble on Ubuntu.  (GNOME uses ESD by default, but I don't use GNOME, and on Ubuntu it seems like ESD is somehow very tightly integrated, so using it outside of GNOME is difficult.)  ARTS is what I use now.  A graphics analogy would be a window manager.

As far as the Audigy, I have no idea.

---

