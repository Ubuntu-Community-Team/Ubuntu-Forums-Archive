---
title: "Strange problem with mPlayer-plugin!"
date: 2005-01-16
forum: General Help
---

### Post by madzzoni on 2005-01-16
Hi There

i just have a strange problem with mplayer/mplayerplug-in.

I got 2 PCs (Laptop and Desktop) with exactly the same ubuntu 4.10 and software setup.
I follow the HOWTO's from [www.ubuntuguide.org](www.ubuntuguide.org) to install multimedia support, and install mplayer-custom and mozilla-mplayerplugin via apt-get.

Al this works perfectly on my Dell laptop, i can see streaming-video's (ex. [http://www.apple.com/trailers/](http://www.apple.com/trailers/) ) and listning to streaming-audio from diffrent radio's.

Today i made exactly the same installation of software in my ubuntu-DesktopPC, but i dosn't work at all.

If i try to see the trailers from the apple.com, the mplayerplug-in starts and counting the download, but at 25% it stops, and then continue download the file without showing the movie! Normally it should start showing the trailer when download is 25%, as it does on my Laptop and my other Debian 3.1 install.

I'll try to re-install everything twice, but nothing helps.
The output from Firefox-browser when typing: about: plugins is identical in both machines.
What can be wrong here???????????????????????

---

### Post by Rancoras on 2005-01-16
It's pretty obvious that there's a difference in the hardware of the two machines.  What hardware is in the desktop machine?

---

### Post by wallijonn on 2005-01-16
Try watching the "small" sized QTime files as opposed to the medium and large.

---

### Post by madzzoni on 2005-01-17
The Desktop PC is a AMD 2500 Barton with nVidia nForce2.

On the same PC i run a debian 3.1 Sarge (Kernel 2.6.8 and nvidia-drivers installed) partition, and  here everything works perfectly.

I use mplayerplg-in 2.66 i all distroes.

---

### Post by Rancoras on 2005-01-17
Hmm, I'm not sure.  There's got to be some minor difference somewhere.  Maybe a package you didn't install on one, but did on another.  I'm at a loss.

---

### Post by madzzoni on 2005-01-17
*Me too...* Mayby i should compile it "the hard" way, following the guide here.

---

