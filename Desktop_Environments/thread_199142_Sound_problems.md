---
title: "Sound problems"
date: 2006-06-18
forum: Desktop Environments
---

### Post by maol62 on 2006-06-18
When playing music in Amarok everything is ok, but when playing in Beep Media Player I get the message "Couldn't open audio". Also the system sound, for example when starting up or shutting down Gnome, is not working. When playing the game GCompris (or other games) there is no sound either. Anyone who's got any ideas?

---

### Post by maol62 on 2006-06-18
Ok, solved it. It seems to be some missconfiguration with the default sound device. I have to edit the properties with the player I'm using so it's not using the default sound device. It is the ALSA-plugin I have to edit so it uses hw 1,0 instead of the default one. But I don't know where to edit this system wide so anyone maybe can help me with that instead.

---

