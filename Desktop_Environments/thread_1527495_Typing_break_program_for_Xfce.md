---
title: "Typing break program for Xfce?"
date: 2010-07-09
forum: Desktop Environments
---

### Post by GordonFreeman on 2010-07-09
Hi,

do you know a tool that forces me to do a typing break like the one in GNOME's keyboard preferences? I did some search on the net but I only found references to GNOME's typing break tool.



Thanks,

Gordon.

---

### Post by squirrelpimp on 2010-09-08
I just found workrave ([http://www.workrave.org/](http://www.workrave.org/)) and will give it a try. Have you found anything similar in the meantime?

Regards, Lars

---

### Post by GordonFreeman on 2010-10-13
> **squirrelpimp said:**
> I just found workrave ([http://www.workrave.org/](http://www.workrave.org/)) and will give it a try. Have you found anything similar in the meantime?

Regards, Lars

Hi,

no, sorry, I gave up back then. But I've found my old thread today on Google and thanks for the tip. Workrave look nice, I'll give it a try :)


Gordon

---

### Post by meinhard on 2011-11-28
Workrave does not have a package in Ubuntu 11.10 unfortunately: [https://bugs.launchpad.net/oneiric-backports/+bug/877074](https://bugs.launchpad.net/oneiric-backports/+bug/877074)

But check out [RSIBreak]("http://www.rsibreak.org/"). It's a bit of an overkill because it launches KDE in the background, but it works.

---

### Post by etienne@egdn.net on 2012-01-21
You can compile gnome2's typing-break and run it stand-alone w/ Xfce4: it finds its way to xfce4's panel and auto-starts at the beginning of a session. I useed gnome-2.30.1 (which probably came from the gnome website) under debian testing (which has the much-disliked gnome3), compiled on my debian computer (you'll need a few g*2.0-dev packages). The only disadvantage is that the gnome-config-editor isn't there, so I should edit ~/.gconf/desktop/gnome/typing_break/%gconf.xml by hand.

  Oops, time for a typing break...

  Hth,

  Etienne

---

