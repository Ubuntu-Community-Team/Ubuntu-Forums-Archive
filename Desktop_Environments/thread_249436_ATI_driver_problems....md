---
title: "ATI driver problems..."
date: 2006-09-02
forum: Desktop Environments
---

### Post by daemonoid on 2006-09-02
Hi,

I've been trying to install the latest ati drivers (8.28.8-1).

I followed this guide:

[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

It looked like everything had gone ok, but whenever i try to play a video (through totem or mplayer) the screen goes to an unsupported mode for a few seconds, then i'm dumped out to the login screen.

fglrxinfo produces correct output when i use it locally, but if i ssh/vnc into it i get:

fglrxinfo
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: unable to open display :0

Strangely, if i use vnc i can watch videos (obviously slowly).

Does anyone have any ideas what could be wrong?

---

### Post by daemonoid on 2006-09-02
I've looked further into this and have found that the problem may be down to a known issue concerning the latest drivers, namely:

"Users with X Server X.org 7.1 can not play any video using XV. The ATI AVIVO Video adaptor is not present."

I'm actually using x11 version 7.0.0-ubuntu but this seems too much of a coincidence.

I'm not exactly sure what this means, but during the setup i did:

sudo aticonfig --overlay-type=Xv

Is this related at all? Are there any other options that would work instead?

---

### Post by daemonoid on 2006-09-02
Ok,

I've got everything working again, videos play fine now that i've removed commented the following line in the /etc/X11/xorg.conf:

#       Option      "VideoOverlay" "on"

This i assume means there's no acceleration going on. I see now why everyone complains about ATI's linux drivers...

Hope this will help someone else.

---

