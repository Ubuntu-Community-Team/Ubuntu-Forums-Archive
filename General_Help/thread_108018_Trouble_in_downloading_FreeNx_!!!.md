---
title: "Trouble in downloading FreeNx !!!"
date: 2005-12-24
forum: General Help
---

### Post by tuxy on 2005-12-24
I am trying to download FreeNx server from the repositories which I found in Ubuntu forums. But, for some reason I can't apt-get update because the server for
seveas.ubuntulinux.nl is not responding. The cursor stays blank for a while and after that I get a message saying 'connection timed out'. But I can ping the seveas.ubuntulinux.nl website. Isn't it strange ?

Following are the URL's in my sources.list to download FreeNx

deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas all
deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas freenx
deb-src [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas freenx 

Is there anything wrong which I am doing?

---

### Post by tuxy on 2005-12-24
I am still waiting for an answer !!! Mean while I have changed the sources.list file and added Kanotix and Debian repositories. When I apt-get update I get the following error:
-----------
Reading package lists... Done
W: GPG error: [http://ftp.au.debian.org](http://ftp.au.debian.org) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F1D53D8C4F368D5D
W: GPG error: [http://kanotix.com](http://kanotix.com) sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FB1A399A71409CDF
W: You may want to run apt-get update to correct these problems
----------

I did apt-get update as it asked me to. But no luck ! Any clues? How to generate a public key ?

Cheers,
tuxy.

---

### Post by btdown on 2005-12-24
I think seveas shut down his repository. there's a message about it in the forums here somewhere...

---

### Post by tuxy on 2005-12-24
OH! Really :( Thx for the info.

---

### Post by sciurus on 2005-12-24
[QUOTE=btdown]I think seveas shut down his repository. there's a message about it in the forums here somewhere...[/QUOTE]

Does anyone have his freenx packages?

---

### Post by tuxy on 2005-12-25
After googling here and there finally I managed to install the FreeNx server ;) It's working great without any fuss.

The repositories can be found by looking into this Wiki page :
[B][https://wiki.ubuntu.com/SeveasPackages](https://wiki.ubuntu.com/SeveasPackages)
[/B]
Few links which are given in that Wiki are not working at the moment. Try using :
**deb [http://mirror.ubuntulinux.nl/](http://mirror.ubuntulinux.nl/) breezy-seveas freenx**

I recommend Nx over VNC. It is really fast and secure.

---

### Post by btdown on 2005-12-25
OMG the wikis are not useless afterall!

---

