---
title: "No sound in Americas Army 2.5"
date: 2006-12-08
forum: Gaming &amp; Leisure
---

### Post by Ted_Smith on 2006-12-08
Hi

I run Americas Army on Dapper. Have done for a while. 

However, having not played it for a few weeks, I tried to the other day and today and on both occasions the sound is not working. I have sound with everything else though, such as when Gnome starts up and to play music via Rhythmbox. But no sound in Amercias Army. 

Tried IRC but no suggestions. Trawled Google and several people have posted the query in various places, but no one has actually been able to answer it. 

Any ideas? 

Thanks

Ted

---

### Post by Ted_Smith on 2007-04-15
This fault still plagues me from time to time. Since posting this thread I have learnt to launch apps from the terminal to capture error messages. When I run armyops I get this : 

```

open /dev/[sound/]dsp: Device or resource busy

```

Does that help anyone troubleshoot my fault? 

I stress that sound works with everything else on my Ubuntu system. 

Thanks

Ted

---

### Post by noerrorsfound on 2007-04-15
Try this:
```
killall esd
```

---

### Post by Ted_Smith on 2007-04-18
That worked!! Thanks a lot!

But that leads me to my next question which is what is 'esd' and how did you know to kill it? Or esd a process of things (thus the use of killall as opposed to kill, I assume?).

---

### Post by AdamG on 2007-04-18
ESD is the "Enlightened Sound Daemon." I had a problem with it a long time ago too, don't remember if I ever found the answer :) The error message you posted indicated that *some* kind of sound daemon was locking your sound device, but I don't know how noerrorsfound knew it'd be esd. Maybe it's got a reputation for that...

As a general rule, you'll almost always use "killall" instead of "kill." I think kill requires a process ID number, which are a pain to look up. Killall just kills based on process names. I've never used kill before, but I use killall pretty often (typically my own misbehaving Python scripts XD).

---

### Post by Ted_Smith on 2007-04-18
Thanks for the clear explanation. 

Regards

Ted

---

