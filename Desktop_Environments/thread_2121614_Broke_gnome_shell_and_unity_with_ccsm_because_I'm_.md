---
title: "Broke gnome shell and unity with ccsm because I'm a slow learner"
date: 2013-03-02
forum: Desktop Environments
---

### Post by Johnny Buffalkill on 2013-03-02
So, I installed ccsm and ran it, hoping to use "vsync" to solve video tearing.  I didn't make any changes though, but now when I try to start gnome shell or unity, I just get a completely blank desktop.  

I did something similar with an older ubuntu version some time ago (hence the slow learner badge) and was able to fix it with "unity--reset", but now I'm in 12.10 and it is deprecated here.

What I've tried so far are:
Setting ccsm to defaults, and then uninstalling it.

"unity-reset" from ppa  per this link:  [http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

Also from the same link:
dconf reset -f /org/compiz/

But none of these have worked.  I still can't get a unity or gnome-shell desktop.  I can only use gnome-classic.  My google searches aren't turning up much beyond what I've already tried.

---

### Post by Frogs Hair on 2013-03-02
I know only of the commands you have posted . Have you tried in TTY ? Ctrl + Alt + F1 and Ctrl + Alt +F7 to return to the desktop.
Compiz can work with Gnome Classic but not with Gnome Shell which uses Mutter.  [http://en.wikipedia.org/wiki/Mutter_(window_manager)](http://en.wikipedia.org/wiki/Mutter_(window_manager))

---

### Post by Mopar1973Man on 2013-03-02
I think you turn off the window decorations.

---

### Post by Johnny Buffalkill on 2013-03-03
The mutter-compiz thing is something I should have known about, in fact,  ccsm did try to warn me that it could break my desktop when I intalled  it.  I keep good data backups and a spare ubuntu installation on my  media drive, so I can afford to be a little brave with the tinkering.   I  tried the commands in both TTY and in a regular terminal and neither  worked.  I think for turning off windows decorations I would have to do  that in ccsm, and I think I'm going to avoid that now.  

I reverted back from proprietary to open source ati graphics drivers, and  now both unity and gnome shell desktops are working.  My graphics  quality is pretty poor, so I suspect things are still screwed up, but at  least now it is usable.  I think I'm just going to live with it unitl  13.04 is released and then do a clean install.  I've been having some  other problems with 12.10 anyway and have been waiting to upgrade.

---

