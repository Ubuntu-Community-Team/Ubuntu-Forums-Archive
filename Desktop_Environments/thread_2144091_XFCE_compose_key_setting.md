---
title: "XFCE compose key setting"
date: 2013-05-11
forum: Desktop Environments
---

### Post by chockopocko on 2013-05-11
Hi there,

I'm an absolute beginner to Linux; I installed Xubuntu 13.04 recently on my laptop, replacing Ubuntu 12.10 - but there isn't any option to set a "Compose" key I can use to quickly type accents.
I've searched it up, and practically all the guides I've found have said to change etc/X11/xorg.conf, which I can't find, or to edit startup files, and I'm not really sure how to do that.

Any help would be much appreciated, thanks!

EDIT: I found this:

*According to [https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey),  for 8.10, there is a XKBOPTIONS= setting in /etc/default/console-setup.  On my 11.10 system, this parameter is now found in  /etc/default/keyboard.*

Because my Dell Latitude D620 doesn't have a right Windows key, I changed it to say ```
XKBOPTIONS="compose:lwin"
``` which effectively made my left Windows key the Compose key. "lalt, ralt," etc. will work with this too.. 

Thanks!

---

