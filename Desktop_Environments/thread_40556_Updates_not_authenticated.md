---
title: "Updates not authenticated"
date: 2005-06-09
forum: Desktop Environments
---

### Post by EmmAytch on 2005-06-09
Hi

Probably a simple one, but when applying updates I get a "can't be authenticated" message.

This is for the 3 latest packages (gedit, gedit-common and linux-image-2.6.10-5-386)

Why?  I have two keys installed Ubuntu Automatic and Ubuntu CD.

I've just switched from Fedora having been on Red Hat Linux since 5.1 so not au fait with Ubuntu yet.

Thanks

---

### Post by Markrian on 2005-06-09
Assuming you've not added any unofficial APT repositories, then all you need to do is update the APT cache:```
$ sudo apt-get update
```Or, if you prefer using Synaptic, just refresh, or reload or whatever it's called.

---

### Post by EmmAytch on 2005-06-09
Tried that (with synaptic).  This is also about the latest security updates.

I have the following repositories:

Ubuntu 5.04 updates (binary and source)
Ubuntu security updates (binary and source)
Ubuntu Hoary hedgehog (binary and source)

All have both Officially supported and Restricted Copyright
The last also has community maintained (Universe)

The two authentication keys are:
Ubuntu archive automatic
and
Ubuntu CD automatic

I did at one point have multiverse but removed it when I found what I was looking for was already in the official.

---

### Post by EmmAytch on 2005-06-10
After more fiddling, it still will not authenticate.

Are there other keys I am missing?  How do I re-install the default keys?

Has anyone else experienced this?

---

### Post by stoneguy on 2005-06-10
As for not authenticating, take a chance :) See [http://ubuntuforums.org/showthread.php?t=33104](http://ubuntuforums.org/showthread.php?t=33104)

There seems to be an inconsistency right now in the upgrades for firefox. I plan to hold off that part until it gets straightened out. It might have to do with the nonavailability of the marillat repositories, which I'd been using. I commented them out of my sources file. I don't know if marillat's been shut down permanently or what.

---

