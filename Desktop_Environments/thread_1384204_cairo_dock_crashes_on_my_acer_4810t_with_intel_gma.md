---
title: "cairo dock crashes on my acer 4810t with intel gma 4500mhd"
date: 2010-01-18
forum: Desktop Environments
---

### Post by kwstas on 2010-01-18
both versions of cairo, no opengl and with opengl seem to work.
sometimes after using the firefox, torrents etc. i hover on the dock and nothing happens!
like it's not there but i just see it.
i see that it's normally running in the "running proceedures" so i kill it.
after trying to understand when exactly gets crashed, i noticed that when for example on a page of firefox, i click the mouse to choose some lines for copying them and that's where the cairo crashes!
that happens with no opengl version too!

i hope someone could help me in this please.

thanks

---

### Post by fabounet on 2010-01-18
which version of the dock are you using ?
there was a bug with the Clipper applet some months ago, that could cause crash like that when you selected some text.
It's been fixed for a while now, so you could just upgrade.

---

### Post by kwstas on 2010-01-18
the version is 2.0.9-karmic1.
i downloaded it yesterday so i think this is the last one.
i tried also to go to the site of cairo but is closed or something...

edit: everything is in french!

i think that clipper was the problem. i just took it off the dock and now it seems alright!
thanks fabounet

---

### Post by fabounet on 2010-01-18
nope it's not the latest, actually it's quite old now, since Ubuntu updates its software every 6 months only, and the development of Cairo-Dock is very active.
so the latest version now is 2.1.3, to be released as soon as the site is back, and it brings a huge number of improvments.

you can get it on Launchpad at the present time. As for the site, it's fully translated in english, and the forum is bilingual ;-)

---

