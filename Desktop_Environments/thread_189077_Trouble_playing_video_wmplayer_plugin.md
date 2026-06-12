---
title: "Trouble playing video w/mplayer plugin"
date: 2006-06-04
forum: Desktop Environments
---

### Post by joplass on 2006-06-04
I can play apple trailers but not this link:
mms://sdmc.contents.edgestreams.net/horsgv/regions/siege/infos/f2/8h/HD_8h_20060602.wmv?WMCache=1&WMBitRate=280000

The link is from [www.france2.fr](www.france2.fr) news 8H, 13H or 20H.  I can play the link in elive but not Drake.
I will appreciate some help. 
Thank you,

---

### Post by yteh on 2006-06-04
My guess is maybe you don't have all the codecs installed... 

If you haven't, you can visit the RestrictedFormats Ubuntu Wiki for details.

---

### Post by joplass on 2006-06-04
[QUOTE=yteh]My guess is maybe you don't have all the codecs installed... 

If you haven't, you can visit the RestrictedFormats Ubuntu Wiki for details.[/QUOTE]

Thanks dude that page did the trick :KS .

---

### Post by wazoo on 2006-06-08
Hmm. Just did the Dapper Drake update (via update manager, which was slick). But when I try an Apple trailer, mplayer loads up to 99% -- then stops.

I did apt-get install the gstreamer0.10-plugins-ugly file, then reload Firefox. mplayerplug-in-qt.so is in the about:plug-ins window, which is supposed to handle the plug-in, right?

Now what?

Thanking you in advance.

---

### Post by joplass on 2006-06-08
try the totem-xine-plugin from synaptic.  just search with totem but the only problem is that you can't play video in full screen mode.

---

### Post by wazoo on 2006-06-12
joplass, I did as you say. But that didn't work -- mplayer again tried to handle it, and again froze. So I REMOVED the mplayer plugin, and let totem handle it. Success! 

Thanks.

---

