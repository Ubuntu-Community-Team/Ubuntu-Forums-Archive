---
title: "Intermittent GAIM sounds"
date: 2005-08-07
forum: Desktop Environments
---

### Post by Ubunted on 2005-08-07
Using 5.04 on my IBM A22m laptop, sound device is a detected Cirrus Logic CrystalClear SoundFusion. My sound effects are intermittent - sometimes they play, sometimes only partly play, sometimes nothing at all. Things like movies and music play fine, so do the login and logout sounds. But all the short little sound effects are spotty.

I've tried switching OSS, ESD and ALSA in various combinations, none seemed to do the trick.

Any ideas?

---

### Post by varunus on 2005-08-07
Have you tried the configure sound properly part of the Ubuntu Guide?  (But don't disable GNOME sounds like that one says to or the sound server startup; you shouldn't need to!)

[http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)

---

### Post by Ubunted on 2005-08-07
Followed it to the letter and I have no sound at all now. "Enable Sound Server Startup" and "Sounds for Events" are both checked.

---

### Post by varunus on 2005-08-07
Does sound come back if you uncheck those two?  Make sure you have everything set to use ALSA or ESD.

---

### Post by Ubunted on 2005-08-07
No dice. All I get is a tone when I test OSS in Default Sink and a "Cannot Construct Pipeline" message for ALSA in Default Source.

---

