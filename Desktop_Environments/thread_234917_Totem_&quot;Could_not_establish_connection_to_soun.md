---
title: "Totem: &quot;Could not establish connection to sound server&quot;"
date: 2006-08-12
forum: Desktop Environments
---

### Post by bjornkri on 2006-08-12
When I try to start Totem it shuts down immediately. 

Totem could not startup
Could not establish connection to sound server

This is the output from running totem from the command line:
- using device default
- using device default
ALSA lib pcm_dmix.c:819: (snd_pcm_dmix_open) unable to open slave
- using device default
- using device default
ALSA lib pcm_dmix.c:819: (snd_pcm_dmix_open) unable to open slave

Everything seems to work ok in my 'main' account (the one with sudo privileges), but the other two accounts on my computer both have this problem. In fact, it seems they don't get any sound at all.

Any ideas?

---

### Post by bjornkri on 2006-08-14
.... never mind. Solved itself.

---

### Post by BramKuijper on 2006-08-14
And... the solution is?

quite curious, since I have the problem also and searching on google pointed me to numerous mailinglist that only provided the problem, but never the answer to it.

---

### Post by kaamos on 2006-08-14
> quite curious, since I have the problem also and searching on google pointed me to numerous mailinglist that only provided the problem, but never the answer to it.

If you have not already done so, try changing audio settings in "gstreamer-properties"

---

### Post by bjornkri on 2006-08-14
I'm not sure, I'm afraid. I tried a few things before giving up... but then next time I rebooted everything worked fine. No clue what did it. Sorry :(

---

### Post by darkalemonkey on 2006-10-23
Hmmm.  I tried to open gstreamer-properties and change the output and input plugins.  ALSA and OSS both give the error:  "could not open resource for writting" ESD gave "could not establish connection to sound server",

---

