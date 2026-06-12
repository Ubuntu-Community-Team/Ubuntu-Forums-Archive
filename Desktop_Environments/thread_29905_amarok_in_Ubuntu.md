---
title: "amarok in Ubuntu"
date: 2005-04-26
forum: Desktop Environments
---

### Post by tara_zw on 2005-04-26
Hi

I'm an ultra newbie with no computer where-with all at all!

Have installed amarok - it's wonderful. But it can't collect ulbum covers etc. I've attempted to put my proxy settings in kcontrol but that hasn't helped. Is there something simple I'm missing?

Oh and I'm behind a firewall - putting the settings in for getting round it into kcontrol doesn't work either.

Thanks!

Tara

---

### Post by alasdair.mccall on 2006-11-22
Howzit Tara,

amaroK is tied into KDE and global proxy settings for KDE (and hence programmes like amaroK) can be set through kcontrol. You'll probably need to download kcontrol using synaptic or apt-get. I found it necessary to download  konqueror (KDE's equivilent of Gnome's nautilus) as well since amaroK seemed to use that too.

Once inside kcontrol, look for Internet Settings and the proxy settings should be there.

Good luck,
Alasdair

---

### Post by taddy_porter on 2006-11-22
Amarok also has issues over samba if you're using it on a network share. I had to mount a samba share as a local directory with RO access to get the build collection to work. There's a wiki on that on Amarok's site if you have this problem too.

---

