---
title: "no available audio device?"
date: 2005-05-31
forum: Gaming &amp; Leisure
---

### Post by Strife on 2005-05-31
If I try to run SDL-based games now, for some reason, it claims that it cannot setup audio properly, so I get no sound/music.

For example, I get the following error on startup of supertux:

```
Warning: I could not set up audio for 44100 Hz 16-bit stereo.
The Simple DirectMedia error that occured was:
No available audio device
```

Trying to enable sound in frozen-bubble, I get this error:

```
Warning: can't initialize sound (reason: No available audio device).
```

This used to work, in fact just yesterday. Restarting didn't solve any problems. I am in the audio group as I should be. I don't recall installing anything that would've messed with the audio settings at all.

Any idea as to what could have caused this?

---

### Post by Strife on 2005-05-31
Okay, I ended up having to install a package that had ALSA support with SDL. I'm still not exactly sure why it was working before though....

---

