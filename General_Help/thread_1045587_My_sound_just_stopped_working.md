---
title: "My sound just stopped working"
date: 2009-01-20
forum: General Help
---

### Post by purplepaint on 2009-01-20
I was listening to music in Rhythmbox, and it was fine.  Then I stopped it, cleared my play queue and closed the program.  Now I can't get any sound at all in any program.

I've tried rebooting and changing every seemingly relevant sound option I can find, and I get no sound through my speakers or when I plug headphones into either of my headphone jacks.

Anyone have any suggestions?

I'm using a Dell Inspiron 1525n laptop running Ubuntu 8.10.

Thanks in advance.

---

### Post by purplepaint on 2009-01-21
Never mind.  It's working again (I have no idea why!).
[B]
EDIT: No it isn't, see below.[/B]

---

### Post by purplepaint on 2009-01-22
The problem's back again.  I plugged in my headphones and the sound slowly faded out until I couldn't get any sound at all through the built-in speakers or the headphones.  Could this be related to the fact that I was advised to edit my alsa-base file in order to record from my mic jack?

I think it was this line I was told I should add to the bottom of the file:

```
options snd-hda-intel model=dell-bios
```

If it's the same as before, my sound should return after one or two restarts, and I assume it'll go away if I plug my headphones in again.

Edit: it was only one line I was advised to add

---

### Post by purplepaint on 2009-01-29
I'm going to bump this thread, because I just plugged my headphones in again and my sound went... again.  I think I'll try removing those lines, although it editing that file solved a massive problem I was having in the first place.

---

