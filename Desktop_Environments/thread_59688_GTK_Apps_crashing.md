---
title: "GTK Apps crashing"
date: 2005-08-25
forum: Desktop Environments
---

### Post by JLTB on 2005-08-25
Hi,

Strange phenomena here ... Whenever I do any of the following all my gtk apps crash.

* Change wallpaper
* Change theme
* Change desktops via Pager

I'm running KDE 3.4.2 with pretty much the newest Hoary everything.  I'm also using the gtk2-qt thing (maybe its that, i dunno).

Some tips are:

Firefox goes through its typical routine and dies with seg fault.
GAIM .. blah blah blah ... seg fault.

It appears that these apps are all getting some similar signal and either the app or GTK is crapping out.

Any ideas?

---

### Post by JLTB on 2005-08-25
anyone having similar problems?

I'm also running Baghira theme, maybe that has something to do with it?

---

### Post by f1dave on 2005-08-26
maybe... freaking baghira... i remember trying to mess around and install that at some stage- then I realised if i wanted a macosx look i could just go and spend a ridiculous amount of money i didn't have on a mac...

So i just mix and match my themes now :P

---

### Post by JLTB on 2005-08-28
Figured it out ...

It was Baghira (grr) ... as best as I can tell Baghira is the only theme I have that uses a bitmap type background on everything (brushed metal).  And since it was being applyed to all the GTK apps via GTK-QT it caused them to freak out.  Every non-bitmaped background theme I have (well every theme actually) doesn't have the problem.

Heh, thats what you get when your theme's are a bunch of uber-powerful C files as opposed to more standardizable XML etc...   :roll:

---

