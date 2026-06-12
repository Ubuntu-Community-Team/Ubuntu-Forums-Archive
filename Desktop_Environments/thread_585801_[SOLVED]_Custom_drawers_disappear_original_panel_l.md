---
title: "[SOLVED] Custom drawers disappear original panel loses all menus and icons"
date: 2007-10-21
forum: Desktop Environments
---

### Post by jludeman on 2007-10-21
I get my drawers and panels all set up the way I like them

Looking good!

Then for no reason they disappear. I searched the forums and found no answers.

I can revert to the default easily enough but what's the point of customizing the panels if
you can't count on them being there through one session even?

This is Ubuntu 7.04. Other than trying to customize the panels I'm just using the default installation.

---

### Post by WiseOdd on 2007-10-23
I having the exact opposite problem. How do you revert to the original panel setup? I went on a customizing spree, then my original panels dissapeared. I tried to make a new one from scratch, but im missing some important things, like the tool for managing my wireless connections...

If you could give me a hand with this, I would be VERY grateful!

---

### Post by jludeman on 2007-10-23
To revert to the original default delete gnome gnome2 gconf gconfd and metacity.
Log off log back on defaults are restored.

---

### Post by jludeman on 2007-10-23
Hey people no replies?
This is pretty serious. I took it as a bug in gnome and decided to try xfce.
So I set up two panels and added some gnome applets with xfapplet.
No crashes from them. Then I added the quick launch applet. Both panels vanished.
Unlike Gnome when I typed xfce4-panel at the command line they came back just as they were.

Still it seems to me there is a bug here of a serious sort.

Any ideas?](*,)

---

### Post by jludeman on 2007-10-25
Solved sort of.

It's not applets in general or gnome or xfce handling gnome applets.
It's an applet.
I had installed an applet called lock keys. I have a wireless keyboard so I thought it would be nice to have a caps lock indicator.

It's kind of a stealth killer. It does not break when installed or used. When some other random thing redraws the desktop in an unkown (to me) way it crashes the panels in xfce and gnome.

I don't really need it so I removed it and everything has been stable for several days and many boot ups.

---

### Post by jludeman on 2007-12-01
Not solved really. Some kind of unresolved bug in gnome panel.

I save .gconfd and .gconf to a backup folder. When the panel configuration breaks I copy them back to my home folder. Problem solved.

---

