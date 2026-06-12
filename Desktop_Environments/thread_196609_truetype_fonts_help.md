---
title: "truetype fonts help"
date: 2006-06-14
forum: Desktop Environments
---

### Post by dimaash on 2006-06-14
I am having problems regestering truetype fonts. I've installed some truetype fonts (msttcorefonts and some ttfs) and edited appropriate config files (xorg.conf, local.conf and etc) and dfontmgr program shows that those fonts are installed and registered yet they dont appear in xfontsel or xlsfonts. Basically X doesnt see them or doesnt recognises them.


I've read plenty of howto's but most of them are outdated. (So please dont give me another link to some XFree86 font howto, cause i am running xorg.) I would appriciate if YOU could provide couple of simple steps that YOU have done to get truetype fonts working. 

Thx.

---

### Post by Zed on 2006-06-14
[Why fonts on Linux aren't straightforward](http://www.tldp.org/HOWTO/Font-HOWTO/notgood.html#xorg)

There are two independent font systems. fc-list will list your TrueType fonts. xlsfonts will list the non-TrueType ones.

---

