---
title: "Argh!! Totem has taken over!"
date: 2005-07-22
forum: Desktop Environments
---

### Post by vassie on 2005-07-22
Help
All my embedded movies in Firefox now want to play in Totem, I was much happier with mozilla-mplayer.
When I open a page with embedded video, I get the following error
```
Totem could not play 'fd://0'.
No URI handler implemented for "fd://0"
```
How can I make them play with mozilla-mplayer again?
Thanks
Ben

---

### Post by Knome_fan on 2005-07-22
Did you install the newest totem from backports staging?
The packages seems to be broke at the moment as totem is using gstreamer even if you install totem-xine, which is the reason why the files don't play I guess.

To get rid of the totem plugin go to /usr/lib/mozilla-firefox/plugins and remove/rename all the libtotem stuff there. (I think the newest totem package install these in the moziall-firefox directory. If that's not the case the files are probably just symlinks to /usr/lib/mozilla/plugins, so deleting the simlinks should do the trick).

---

### Post by vassie on 2005-07-22
[QUOTE=Knome_fan]Did you install the newest totem from backports staging?
The packages seems to be broke at the moment as totem is using gstreamer even if you install totem-xine, which is the reason why the files don't play I guess.

To get rid of the totem plugin go to /usr/lib/mozilla-firefox/plugins and remove/rename all the libtotem stuff there. (I think the newest totem package install these in the moziall-firefox directory. If that's not the case the files are probably just symlinks to /usr/lib/mozilla/plugins, so deleting the simlinks should do the trick).[/QUOTE]

Yes, I installed the one from backports staging, I'll try removing the totem stuff later, at work at the moment :(

Thanks

Ben


*Edit. That fixed it, your a star :):):)

---

