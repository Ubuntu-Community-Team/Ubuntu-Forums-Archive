---
title: "Audio turns off when I XDMCP"
date: 2005-03-25
forum: Desktop Environments
---

### Post by TurboStar on 2005-03-25
I'm using my Ubuntu box via XDMCP from the computer next to it.  When I log in this way I do not get any audio.  If I log in locally the audio works just fine.

I think gdm or enlightenment may be turning off audio somehow when XDMCP is detected.  I just can't find where to bypass this.

I don't need to tunnel the audio over the network.  I just want it to come out the sound card like it does when I log in locally.

thanks

---

### Post by TurboStar on 2005-03-27
Took a bit of searching.  Seems Esound wants to forward the sound over the network when it sees $DISPLAY set.  I snubbed it by adding this to ~/.gnomerc:

export ESPEAKER=localhost

Had to track this down by way of source code.

---

