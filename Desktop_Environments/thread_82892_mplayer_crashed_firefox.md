---
title: "mplayer crashed firefox"
date: 2005-10-27
forum: Desktop Environments
---

### Post by caporaso on 2005-10-27
Has anyone out there experienced a problem in firefox where mplayer will load fine, and play a video without any issues, but once you attempt to leave the page (for example, by hitting 'Back') firefox crahses?  If anyone has figured this one out I'd love to hear how you did it, or if anyone has any suggestions of things I might try to fix this, that would also be greatly appreciated.

I've tried removing and reinstalling the mplayer-plugin for firefox with the package manager, and oddly, even after removing it, a plug-in still exists, although I'm not sure where (ie. I remove the plugin, go to a page that would use mplayer, and mplayer still loads, and I have the same issue).

Thanks in advance for any suggestions -- I've checked around the forum and haven't found anyone else with a similar issue, but if there is a discussion out there about this just point me at it!

---

### Post by the_purulent on 2005-10-27
This problem ocassionaly pops up for me.  I have not been able to find a fix as of yet, but it's not a show stopper.  I don't stream alot of media as it is right now (aside from audio).  

But a fix would be nice! :D

---

### Post by adis on 2005-10-27
I had this problem with mplayerplug-in 3.05 and 3.11. With mplayerplug-in CVS the situation seems better, it is much more stable (for me at least). To compile it follow the instructions: on [http://mplayerplug-in.sourceforge.net/install.php]("http://mplayerplug-in.sourceforge.net/install.php").
If you are a lazy boy :) you can use the one I compiled (see attachments).

Cheers,
adis

---

### Post by caporaso on 2005-10-28
Thanks for your responses, I think I may have figured it out. It seems like install the firefox-dev package, and then the mozilla-plugin package fixed the issues. So:

1) remove the mplayer-plugin package if its installed
2) install the firefox-dev package
3) install the mplayer-plugin package

That's worked for me so far, if the issue pops up again I'll post again.



Thanks!
Greg

---

### Post by Remmelas on 2005-10-28
Nicely found, fixed my issues as well =)

---

