---
title: "Need to grab the raw audio stream coming from a program"
date: 2006-06-24
forum: Desktop Environments
---

### Post by enigma_0Z on 2006-06-24
Hi all,

Basically, I need a program or method of getting the raw audio stream coming from a program. I can format it from there. Is there some way of doing this? It would be best if I could redirect it into a file. A program that redirects audio output from a program into a file instead of heading to /dev/dsp would work also. Anything that would work? Thanks.

---

### Post by aysiu on 2006-06-24
Audacity?

Or...
[http://ubuntuforums.org/showthread.php?t=28356](http://ubuntuforums.org/showthread.php?t=28356)
[http://www.ubuntuforums.org/showthread.php?t=169278](http://www.ubuntuforums.org/showthread.php?t=169278)

---

### Post by enigma_0Z on 2006-06-24
hah. Tried that. Perhaps I've got a problem with my sound setup.

I want to record some sounds coming out of firefox, if that helps. If i've got them playing, I can't record them in audacity... I get the following errors:

```
PaHost_OpenStream: could not open /dev/dsp for O_RDONLY
PaHost_OpenStream: ERROR - result = -10000
```

It's because the device is busy (playing something) right? So what am I missing?

... (edit) ...

BUT, it looks like vsound might give me what i want! thanks.

... (/edit) ...

---

### Post by aysiu on 2006-06-24
"Tried that" means Audacity...? Or both of the links I linked to as well?

---

### Post by enigma_0Z on 2006-06-24
Sorry. I mean that I tried audacity. I assumed that the links you had up were just more audacity stuff... BUT vsound works beautifully. Thanks.

---

