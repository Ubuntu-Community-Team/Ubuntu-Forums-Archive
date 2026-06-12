---
title: "gnome-terminal + compiz: is &quot;fake transparency&quot; possible?"
date: 2008-03-02
forum: Desktop Environments
---

### Post by John C. Wright on 2008-03-02
I've just installed Ubuntu 7.10. In previous versions, setting gnome-terminal's background to "transparent" would use a kind of "fake transparency," where the background of the terminal was set to the appropriate subsection of the desktop background image. In 7.10 with compiz, it becomes truly transparent, with icons and other windows appearing in the background as well.

The issue is that (for me, at least), the fake transparency was eminently usable, while the real transparency isn't. It's easy to set a desktop background and terminal foreground color that are readable together. Other windows, however, can be of any color. For example, using the stock "Elephant" background, I can use a white font in the terminal. With real transparency, a white window such as this Firefox here will cause the text in the terminal to be unreadable.

So -- is there a way to have the "fake transparent" effect with the new Compiz desktop? 

Many thanks,
JCW

---

### Post by kdarkentity on 2008-03-02
One way to do that is to disable the advanced settings of compiz , so go to system/preferences/appearance and then go to the last tab in the appearance window and select "none"

i know theses aren't the best instructions but i'm not booted into linux right now.

Also you could switch your windows manager to metacity, just open up a terminal and type metacity --replace.

I hope this helps.

---

### Post by John C. Wright on 2008-03-04
Thanks for the tip. I feel, however, that disabling Compiz would be throwing out the baby with the bathwater. I love the window manager effects. Are you perhaps aware of a different terminal application that supports "Fake transparency" and either isn't Composite-aware or allows you to disable the latter?

Thanks again.
JCW

---

### Post by HyugaRicdeau on 2008-07-07
I'd like to bump this, though I think this is less Ubuntu's problem and something to report to Gnome.  I guess gnome-terminal checks the window manager and enables this functionality.

I basically agree with the original poster though--real transparency is nice, but it would be better if it just showed through to the background, instead of showing other windows.  Much more useful that way.

---

