---
title: "Is kmplayer for kubuntu only or can it work with Ubuntu as well?"
date: 2006-08-05
forum: Desktop Environments
---

### Post by xp_newbie on 2006-08-05
After realizing that neither Totem Movie Player nor VLC can play videos made for Windows Player, I am looking now to install mplayer.

However, synaptics shows only kmplayer as available - which I don't whether works with Kubuntu only.

Can it work with Ubuntu? Should I go ahead and install it without fearing that it will damage something in the system (as in Windows registry...) ?

Thanks,
Alex

---

### Post by kerry_s on 2006-08-05
Did you add the gstreamer-ugly codecs to totem? Did you add the repo for mplayer? Yes, you can use kmplayer but it will bring kde dependencies.

# mplayer
deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free

---

### Post by xp_newbie on 2006-08-05
> **kerry_s said:**
> Did you add the gstreamer-ugly codecs to totem? Did you add the repo for mplayer? Yes, you can use kmplayer but it will bring kde dependencies.

# mplayer
deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free


Kerry, thanks for your reply. You asked quite a few questions, so here are the answers:

1. Yes, I added the gstreamer-ugly codecs to totem, but totem complains with the error message **No URI handler implemented for "mms"**. Any idea whether Totem can play URIs that start with 'mms://' ?

2. I just added Multiverse to Synaptics and it found mplayer. My question now is can I "get away" with using Totem+gstreamer only, or do I really need mplayer to be able to play everything? If the latter (mplayer claims to be "The Ultimate Movie Player For Linux"), then why isn't it the default player (instead of Totem) in Ubuntu? Are there any issues with it?

Thanks,
Alex

---

