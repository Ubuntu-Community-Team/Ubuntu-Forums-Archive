---
title: "lmms question"
date: 2005-12-26
forum: General Help
---

### Post by Odinist on 2005-12-26
I can't seem to get any sound output from lmms, regardless of what I choose as the output. For those of you using this program, how do you have it setup?

---

### Post by Odinist on 2005-12-26
::bump::

---

### Post by mcduck on 2005-12-27
I've set it to use ALSA, with 'default' as the device and 2 channels. Works fine for me.

Try running 'killall esd' and then start LMMS. If that works, you could go to System/Preferences/Sound and disable the 'Enable sound server startup'

---

### Post by Odinist on 2005-12-27
Thanks for the response!

I had tried stopping esd, but I'm not sure if I'd had it set to use ALSA at the time... I'll try it when I get home (I'm at work on a stupid Windoze machine. Bleh.)

---

### Post by Zyphrexi on 2006-10-27
worked fine in dapper, now I get static when playing ogg. Don't understand it.

---

