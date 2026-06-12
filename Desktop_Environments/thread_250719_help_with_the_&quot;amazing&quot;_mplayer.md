---
title: "help with the &quot;amazing&quot; mplayer"
date: 2006-09-04
forum: Desktop Environments
---

### Post by boast on 2006-09-04
My mplayer would play streams choppy (it worked fine on totem.) So i decide to download the mplayer svn. Problem is, now when I try to stream [http://www.crtvg.es/asfroot/television.asx](http://www.crtvg.es/asfroot/television.asx) I get a "Couldn't resolve name for AF_INET6:www.crtvg.es"

Also, when I go to mplayers config, I don't see alsa in the audio drivers, only oss pcm mpegp.

I also can't play music/movies from my network. In the config it showed yes for samba support. Totem plays the media fine through the network. Mplayer just stands still when I select to open the file with mplayer.

I also get a "cannot load bitmap font: /usr/share/mplayer/font/dont.desc" error. How do I fix this.


I don't expect to get help from here, since I usually never get a responce. But thanks in advance anyways.

---

### Post by berserker on 2007-01-12
> **boast said:**
> I also get a "cannot load bitmap font: /usr/share/mplayer/font/dont.desc" error. How do I fix this.

Use ```
--disable-bitmap-font
``` during configure

---

