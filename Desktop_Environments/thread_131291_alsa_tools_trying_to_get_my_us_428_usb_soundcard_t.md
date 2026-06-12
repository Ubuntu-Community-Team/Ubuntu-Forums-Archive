---
title: "alsa tools? trying to get my us 428 usb soundcard to work.."
date: 2006-02-16
forum: Desktop Environments
---

### Post by bobbyshane on 2006-02-16
ok.. my us-428 seems to be "installed" however I can neither playback nor record from it. Looking through some alsa documentation it appears that I need to install alsa tools and the firmware for my device to work properly. However I attempt to install alsa tools and have ran into a problem with a dependency. I tried installing alsa tools 1.0.9rc2. When I follow the directions for installing the tools it errors saying 

"checking for libasound headers version >= 1.0.0... not present.
configure: error: Sufficiently new version of libasound not found."

however I have libasound 2 (1.0.9-2) installed in synaptic
do I need to install a different version of tools or libasound? I'm so confused.
If anyone could help me out here it would be much appreciated. Thanks.

---

### Post by christhemonkey on 2006-02-16
alsatools version 1.10.0-1 is in the repositories is it not?
so unmet dependencies can be installed easily?

---

### Post by bobbyshane on 2006-02-16
[QUOTE=christhemonkey]alsatools version 1.10.0-1 is in the repositories is it not?
so unmet dependencies can be installed easily?[/QUOTE]


If it's in the repositories it's under a different name.. is it in the repositories in your ubuntu installation? I added universe and multiverse and still didn't find one mention of alsa tools except libclalsadrv which is a development package for alsa. Any further help would still be appreciated however.

---

### Post by christhemonkey on 2006-02-17
I think its under alsa-tools.
[http://archive.ubuntu.com/ubuntu/pool/universe/a/alsa-tools/](http://archive.ubuntu.com/ubuntu/pool/universe/a/alsa-tools/)
My ubuntu box aint on the tinternet, so thats where i would of downloaded it from.

---

### Post by bobbyshane on 2006-02-17
thanks!

---

