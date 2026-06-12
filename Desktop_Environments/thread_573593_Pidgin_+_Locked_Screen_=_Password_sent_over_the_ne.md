---
title: "Pidgin + Locked Screen = Password sent over the network"
date: 2007-10-11
forum: Desktop Environments
---

### Post by ozymo on 2007-10-11
So, I've had an interesting new development.

I'm running Gutsy, with all the latest updates, and I'm at work, so locking my screen is a necessity.  I'm running XGL with effects on an ATI card.  I use synergy to connect my stuff together.

When I lock my screen, all is well until I come back to unlock it.  Apparently, the passwiord dialogue box is not automatically selected, so i type my password, hit enter, and "
"beep".  No go.

So, I click in the box, type my password, hit enter, and return to my session.

I noticed today that someone I was talking to on pidgin was asking me why i kept typing the same random characters over and over.

It turns out, that the first time I type my password, not in the dialogue box, it is apparently being transmitted through pidgin.

Any clues or bugs that anyone knows about on the   I did a quick search around launchpad, but found none.

Cool.

Thanks,
Chuck

---

### Post by kostkon on 2007-10-11
It looks like a very strange bug, indeed. It would be very good if you could fill a bug report at Launchpad. :)

---

### Post by Nubbie on 2008-04-02
this actually happened to me a couple times... i think i pegged it down to a focus stealing option in what was then beryl... yeah, i'm only commenting because I also found this behavior weird.

Even more disturbing is pidgin storing your passwords in a plain-text file.

---

