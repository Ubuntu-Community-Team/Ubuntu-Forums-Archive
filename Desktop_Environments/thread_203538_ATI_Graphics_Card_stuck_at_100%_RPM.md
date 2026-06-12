---
title: "ATI Graphics Card stuck at 100% RPM"
date: 2006-06-25
forum: Desktop Environments
---

### Post by v8YKxgHe on 2006-06-25
Hey, 

When I install the FGLRX Graphics Drivers for my X800XT, my graphics card fan is stuck at 100% RPM which is quite loud. Is there anyway of limiting it?

---

### Post by v8YKxgHe on 2006-06-26
Anyone? It's really loud and makes me want to go back to Windows!

---

### Post by nquinnathome1 on 2006-06-26
Hmm that's odd and i've not heard of it before; if it only does it in Linux then I would assume that it's a bug in the ATI driver; is it possible for you to run ubuntu with the card using another driver?

---

### Post by v8YKxgHe on 2006-06-26
Yes, When I use the default Mesa( or Vesa? which one is it lol ) it's fine, the fan will adjust it's RPM to the temperature of the GPU Core, but with the FGLRX drivers it's stuck at 100%. 

Like I said, it's amazingly loud and so for now I'm going to use Windows untill I can fix it.

---

### Post by Ramses de Norre on 2006-06-26
You could try to install the newest drivers from the ati website, if it's a bug it may be fixed.

---

### Post by v8YKxgHe on 2006-06-26
Well I just tried that, I uninstalled my FGLRX drivers - changed fglrx to ati /etx/X11/xorg.conf and now it's fubar. It wont load X. Why can't Linux just work!

---

### Post by ricesteam on 2008-01-30
I had this problem since 6.06.  I've always searched for possible solutions only to find people reporting the same problem.  It seems that there is still no fix yet as there are many posters posting the same problems and no replies to the threads other than "me-too's".

I think it's more of a driver issue than a bug since the problem still exists.  Unless there are not enough people with the problem for the dev to feel the need to fix this "bug".

---

