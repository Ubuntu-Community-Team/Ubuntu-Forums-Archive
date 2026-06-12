---
title: "RealPlayer menu very s-l-o-o-o-w during playing..."
date: 2006-03-03
forum: Desktop Environments
---

### Post by hajk on 2006-03-03
Installed RealPlayer 10 as per the Ubuntu Wiki, and it plays fine, both audio and video streams. Only problem: the menu items and stop/pause buttons in the RealPlayer window become agonizingly slow once the streams are running. It may take 30 seconds or more for the pause button to react, or for the Favorites menu to open, for example. Yet, once the stream stops, these items are as snappy as ever.

System monitor shows no heavy CPU load (I have dual Opterons), and no high memory use (I have 2GB RAM) -- so what could cause this lack of response?

---

### Post by scorcher on 2006-03-03
I do not know what causes the slowness.

I fixed it on my machine by downloading a nightly build of realplayer.
[http://forms.helixcommunity.org/helix/builds/?category=realplay-current]("http://forms.helixcommunity.org/helix/builds/?category=realplay-current")

It fixed the slowness and has ALSA drivers.

---

### Post by hajk on 2006-03-03
Thanks for the link! 

It is really puzzling, when I return from another virtual Gnome screen the contents of the RealPlayer window are blanked out, only to reappear after some 15 seconds or so. I tried to play with the Tools-->Preferences settings, no dice. Thinking that it might be an X-driver issue, I even switched from the "nv" driver to "nvidia" -- still no change. All the while no problems with other applications... I had already come to the conclusion that it must be RealPlayer itself, in my case the .deb from the Marillat repository (for etch). Your experience confirms that, so I'll follow your suggestion.

---

