---
title: "Gnome Global Menu Bar help."
date: 2009-05-22
forum: Desktop Environments
---

### Post by Vord on 2009-05-22
I just finished up installing the gnome global menu bar, and I'm noticing that when I have a nautilus window open, the program name on the menu reads "CD/DVD Creator" instead of what I'd expect it to say along the lines of "Nautilus" or something similar. I've got a screen shot in case I'm not being clear enough (Entirely possible, haven't slept)

Anybody run into this issue?

---

### Post by Vord on 2009-05-22
Used a quick fix after referencing this bug report

[http://code.google.com/p/gnome2-globalmenu/issues/detail?id=386](http://code.google.com/p/gnome2-globalmenu/issues/detail?id=386)

I removed the CD/DVD Creator launcher from the menu, but if anybody has a more permanent workaround that causes less inconvenience, feel free to enlighten us :)

---

### Post by Psychopump on 2009-05-22
Sorry, I am not answering your question...

Did you find a deb package for the global menu bar or compile it yourself?
(I am still baffled by compiling)

---

### Post by Vord on 2009-05-22
> **Psychopump said:**
> Sorry, I am not answering your question...

Did you find a deb package for the global menu bar or compile it yourself?
(I am still baffled by compiling)

I dug up a deb for it. Want me to track it down again and give you a link?

Or better yet, you want me to teach you how to compile? :P (Honest offer, I have nothing to do today)

---

### Post by Tibuda on 2009-05-22
> **Psychopump said:**
> Sorry, I am not answering your question...

Did you find a deb package for the global menu bar or compile it yourself?
(I am still baffled by compiling)

[https://launchpad.net/~globalmenu-team/+archive/ppa](https://launchpad.net/~globalmenu-team/+archive/ppa)

---

### Post by Bohemenian on 2009-08-01
If someone is still looking for a work-around, I just added an entry "File Manager" to the GNOME Main Menu, from what I read that's where globalmenu looks for the app's titles. Since CD/DVD Creator is part of nautilus, globalmenu assumes nautilus should be called CD/DVD Creator.

But as I said, seems to work for me by adding a launcher titled "File Browser" (or whatever you want to be displayed instead of CD/DVD Creator) with the command nautilus in the "Applications"-menu (think that's called GNOME Main Menu too).

---

