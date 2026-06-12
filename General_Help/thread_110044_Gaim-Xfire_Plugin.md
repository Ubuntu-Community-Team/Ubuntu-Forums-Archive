---
title: "Gaim-Xfire Plugin"
date: 2005-12-29
forum: General Help
---

### Post by Drunken Pirate on 2005-12-29
I am trying to install Xfire for Gaim, and its complains that it cant find the right gaim folder. I downloaded the source from the GAIM CVS, but there isn't a gaim.pc in there. What should I do?

checking for gaim... Package gaim was not found in the pkg-config search path. P erhaps you should add the directory containing `gaim.pc' to the PKG_CONFIG_PATH environment variable No package 'gaim' found


Heres the command I used to run configure:
sudo ./configure --with-gaim=/home/brent/.gaim-source/gaim/plugins --prefix=/usr


EDIT: I fixed it. Instead of using the source from gaim, i install gaim-dev, and it compiled fine. Now to try make and make install!

Well is seems to have worked. No one is online now, so I cant test. Anyone got this to work?

---

