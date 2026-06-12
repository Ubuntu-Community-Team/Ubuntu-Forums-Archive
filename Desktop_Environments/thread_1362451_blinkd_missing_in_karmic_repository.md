---
title: "blinkd missing in karmic repository"
date: 2009-12-23
forum: Desktop Environments
---

### Post by raziv on 2009-12-23
Hi,
I've noticed that package blinkd (as they say, good things come in small packages...) [was omitted in the karmic repository]("http://packages.ubuntu.com/search?keywords=blinkd").
As for me, the use of blinkd with a mail notifier (say, [checkgmail]("http://checkgmail.sourceforge.net/#faq")) is a very nice upgrade to my pc usability - is there an alternative?
Thanks,
raziv

---

### Post by Rhubarb on 2009-12-23
You can just use the blinkd from Jaunty:-
[http://packages.ubuntu.com/jaunty/blinkd](http://packages.ubuntu.com/jaunty/blinkd)

Or, you could try out **ledcontrol** in the karmic repos
(not sure if ledcontrol can do all that you want, as I've never tried it before).

---

### Post by raziv on 2009-12-23
Thanks!
The jaunty version worked fine (from binary package only - trying to install from source didn't work for some reason...).
I just wonder then why it was removed from the karmic repository...

---

### Post by Rhubarb on 2009-12-23
[this]("http://osdir.com/ml/debian-bugs-closed/2009-05/msg00729.html") would be why blinkd isn't in karmic anymore

Basically upstream is incontactible, it doesn't get downloaded much (low popcorn rating), and no other app in debian (and hence ubuntu) requires it.

Though obviously atleast 1 person uses it ;)

---

