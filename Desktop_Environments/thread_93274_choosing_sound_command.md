---
title: "choosing sound command?"
date: 2005-11-21
forum: Desktop Environments
---

### Post by akurashy on 2005-11-21
I have this problem that the app can't do the sound successful, i'm using the command, aplay, is there one for alsa to mix etc etc?

---

### Post by 23meg on 2005-11-21
"play" is the most common command, but if you specify which app this is and what exactly you're trying to do, maybe we can be of more help.

---

### Post by akurashy on 2005-11-21
I compiled Gaim2 cvs some mins ago, and installed it, yes I know there are warnings about using CVS, well anyway, it looks like gaim2 removed the automatic option in the sound.

---

### Post by 23meg on 2005-11-21
Does "play" help? Maybe you should ask in the Gaim mailing list.

---

### Post by akurashy on 2005-11-21
well play works, but it kinda goes play in a delay =/

---

### Post by 23meg on 2005-11-21
Maybe playing (pun unintended) with the buffer size / sampling rate will help; type "man play" for details.

---

