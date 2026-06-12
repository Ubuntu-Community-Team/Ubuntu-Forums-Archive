---
title: "playing dvds problem/question"
date: 2006-08-08
forum: Desktop Environments
---

### Post by Westerberg on 2006-08-08
when I try to play a dvd in totem, I get the following message
> Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.
Following recommendations in other posts, I was going to install totem-xine.  (Seems I recall a recent upgrade removed totem-xine in favor of totem-gstreamer, although my memory is a little hazy.)But when I go to install totem-xine via CLI, I get this message among others:
> The following packages will be REMOVED:
  totem totem-gstreamer ubuntu-desktop

Remove ubuntu-desktop?  That sounds disastrous.
Could someone give me some guidance so I can play a dvd?

---

### Post by vijirajan on 2006-08-08
Its not as disastrous as it sounds :) ubuntu-desktop is a meta package that can safely be removed after installing Ubuntu. It only removes ubuntu-desktop and nothing else. So go ahead and install totem-xine.

---

### Post by bscbrit on 2006-08-08
Have you installed libdvdcss?  It isn't automatic because in some countries its use is illegal.  The more enlightened places, though, allow it to be used. :D 

But by all means change back to xine.

---

### Post by Westerberg on 2006-08-08
okay i installed totem-xine, thereby removing totem-gstreamer and ubuntu-desktop.  dvd play is possible and everything seems to be working ok.  Thanks

---

