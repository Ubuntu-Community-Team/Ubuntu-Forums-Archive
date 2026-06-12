---
title: "turn off tool tips?"
date: 2007-07-05
forum: Desktop Environments
---

### Post by aacs on 2007-07-05
Hi all!

Can you tell me a way to turn off all tool tips "globally" (in Gnome)?
These are annoying because the tips very rarely contain any
useful information. It is OK for people getting to know the
desktop, what the icons do etc. but in general they just spoil
the interface.

Thank you!
Andras

---

### Post by AZzKikR on 2007-07-05
Spoil the interface, you got to be kidding me? Excuse me, but in my opinion you are just making a big deal out of nothing. You don't see them unless you are hovering over a widget for more than 1 second. They don't spoil anything if you ask me and are in fact very useful. And I am an experienced Gnome user.

As for a solution, I wouldn't have an answer on that, sorry. Perhaps the gconf-editor has something regarding tooltips.

---

### Post by aacs on 2007-07-05
For me, sometimes there is that ~1sec delay, sometimes they pop instantly.
I did not mean they are useless for everyone but beginners, that was just an example,
sorry if I offended you. I just would not miss tooltips at all.
Anyway, thanks for the idea.

---

### Post by AZzKikR on 2007-07-05
Nah I wasn't offended, I was just flabbergasted by your question :D

---

### Post by bapoumba on 2007-07-05
> **aacs said:**
> Hi all!

Can you tell me a way to turn off all tool tips "globally" (in Gnome)?

gconf-editor > apps > panel > global > untick tooltips _enabled.

---

### Post by alarclin on 2008-07-23
I know this is an old thread, but I just want to thank aacs for asking a question that saved me yet more googling, after I already wasted an absurd amount of time hunting here and there in gnome's interface settings to try to find a feature so obvious that I'm flabbergasted, to borrow AZzKikR's term, that it isn't simply included in the main preferences. (Cool handle there, AZzKikR, does it indicate why you're on these forums, just to give a good *** kicking to people who ask perfectly reasonable questions? I mean, how dare they? You are too easily "flabbergasted.")

and thanks to bapoumba for providing a partial answer. I suppose however I have to dig through some other part of that idiotically-designed gconf-editor to find the settings, if they exist, for turning off the tool-tips for the window decorations.  I mean really, most people pretty quickly figure out that the "close window" button is for closing the window! 

Any unnecessary visual clutter does spoil an interface if it can't be adjusted. If it doesn't bother the asskickers out there, fine. But why is it any skin off your nose if other people want an option to reduce the clutter?

---

### Post by alarclin on 2008-07-24
Christ almighty, I unchecked the item that bapoumba mentioned, and yet the tool-tips are *still* appearing in the freaking panel. 

I give up. 
This page, for those who care, demonstrates that aacs and I are hardly alone in finding this a nuisance: 

[http://geekybits.blogspot.com/2007/07/ubuntu-tip-turning-off-tooltips.html](http://geekybits.blogspot.com/2007/07/ubuntu-tip-turning-off-tooltips.html)

Gnome developers, please!  Give us some basic control over the interface! 

And for God's sake, give gnome a decent window manager. Metacity makes Os X seem usable, and M$ window-management looks downright intelligent, in comparison, And that's very sad.

---

