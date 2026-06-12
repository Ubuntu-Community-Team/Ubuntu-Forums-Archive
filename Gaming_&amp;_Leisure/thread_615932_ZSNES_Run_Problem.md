---
title: "ZSNES Run Problem"
date: 2007-11-17
forum: Gaming &amp; Leisure
---

### Post by liquidypoo on 2007-11-17
I've been able to run ZSNES fine in the past, but now whenever I attempt to start it, the window appears, then immediately closes.  I've tried running it using alt+f2, and I've tried uninstalling and reinstalling it.  I'm still new to Ubuntu, so I have no idea what else I can do.

---

### Post by disturbedite on 2007-11-17
when this happens (a million times a day) will ppl please post the output while trying to launch from command line/term?

---

### Post by liquidypoo on 2007-11-17
Well, like I said, I'm still new to Ubuntu.  How do I even see the output when I try to run it using alt+f2?

---

### Post by B00R4dL3y on 2007-11-17
If you just installed Gutsy and pulled ZSNES from the repos then it probably won't start.  I did the same and I think it complained about some file/directory not being there.  I think I did the trick to force it to use the alsa sound driver to get things going.

Press ALT + F2 or from a Terminal window enter:

```
zsnes -ad alsa
```

If that doesn't work then you'll have to do some more searching.

---

### Post by liquidypoo on 2007-11-17
That did the trick!  Thanks for the help.

Granted, I have no idea if this had anything to do with it, but the terminal did have some weird output before it actually opened ZSNES:

```
Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event10. Make sure you have read permissions to it.
Unable to poll /dev/input/event9. Make sure you have read permissions to it.
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.

Audio Opened.
Driver: Advanced Linux Sound Architecture (ALSA) output
Channels: 2
Rate: 32000

ZSNES could not find any joysticks.
```

---

