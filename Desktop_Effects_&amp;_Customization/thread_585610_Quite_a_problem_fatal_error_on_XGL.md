---
title: "Quite a problem: fatal error on XGL"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by eoghanmurray on 2007-10-21
I've just built a custom media centre PC based on some old components I had lying around and a new case. Everything went fine as wiped Vista Basic (which came with the hard drive bundle for some bizzare reason) and installed Feisty (I'm happy with it and am only using Gutsy on my development machines.) Installed fine, everything went smoothly, installed a few applications. Supertux looks brilliant on the TV and even completed Tutorial Island on Pingus (I know, I'm sad :( ) - but one thing bothered me - effects. I have an ATI X600 card (128MB - ancient, I know ;) ) and got Compiz Fusion running brilliantly before on that card but on a different system. Now, when I log in under GNOME with XGL, and launch '**compiz --replace**', XGL crashes and I revert to the login screen. No error message or anything! Anyone got a solution? It's a media centre so it should be slick, and I'd be SO grateful if someone had an answer.

BTW, Pentuin 4 3.0GHz, 768MB RAM, ATi X600 128MB, 500GB SeaGate HDD

Thanks for any help!

---

### Post by eoghanmurray on 2007-10-21
**UPDATE**
Got it sort of working by tweaking my xorg.conf file - but here's what I get.

```
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libccp.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'ccp'
```

That, my friend(s), is progress. No dead X. Good :D

---

### Post by eoghanmurray on 2007-10-22
Anyone, please? B glad of any tips etc...

---

