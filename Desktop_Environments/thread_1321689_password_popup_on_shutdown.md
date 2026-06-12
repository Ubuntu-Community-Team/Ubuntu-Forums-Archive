---
title: "password popup on shutdown"
date: 2009-11-10
forum: Desktop Environments
---

### Post by perixx on 2009-11-10
the trouble:

there's a password entry pop-up every time i try to shutdown xubuntu karmic...

since i've installed a few things (not mythtv) right after installation, i don't know if any of those apps might be responsible for that (and why) or if this is default behaviour of karmic.

i've checked the active sessions, but there was only the current one. the 'mythtv'-thread doesn't apply here.

how can i get rid of that?

EDIT:
The popup was obviously eliminated by the magic keys and a reboot...

---

### Post by Optimus72 on 2009-11-11
How did you solve this? I have the same problem.

What magic keys are you referring to?

---

### Post by perixx on 2009-11-11
Ah, well the 'magic keys', they are provided by the Linux kernel as a last resort for a clean shutdown; if everything else is frozen, this still works most of the time and ensures, among other things, that all drives are unmounted correctly.

It's a rather tricky combo, which you'll need both hands for:

```
Press (alltogether) ALT + CTRL + PRINT + R + E + I + S + U + B
```

After this, the system rebooted and I circumvented the popup. 
It didn't show up again, since that.

perixx

---

### Post by Optimus72 on 2009-11-13
That didn't work for me. The system rebooted, but the popup remains...

---

### Post by perixx on 2009-11-13
Hmm, sorry to hear that...


But I couldn't quite figure out, why it happened to me in the first place...
I've seen some post probably about the same symptom, where someone installed mythtv and there was a second session running due to this. 
But the problem was gone before I could investigate any further:
[http://ubuntuforums.org/showthread.php?t=1299948](http://ubuntuforums.org/showthread.php?t=1299948)

There was another one having this problem some time ago, I see:
[http://ubuntuforums.org/showpost.php?p=7794500&postcount=1](http://ubuntuforums.org/showpost.php?p=7794500&postcount=1)

And another one, this looks very interesting, sort of we have a bug here:
[http://ubuntuforums.org/showthread.php?t=1199801&highlight=password+shutdown](http://ubuntuforums.org/showthread.php?t=1199801&highlight=password+shutdown)

regards, 


perixx

---

### Post by Optimus72 on 2009-11-13
Uninstalling MythTV solved my problem. I installed it a while ago, but never used it. The popup didn't show up until I upgraded to Karmic.

Anyway, thanx for the help.

---

### Post by perixx on 2009-11-13
good that you solved your problem :)

---

