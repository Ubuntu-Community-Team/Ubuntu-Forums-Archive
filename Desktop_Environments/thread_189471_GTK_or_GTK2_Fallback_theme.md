---
title: "GTK or GTK2? Fallback theme?"
date: 2006-06-05
forum: Desktop Environments
---

### Post by DanielSwe on 2006-06-05
Hi
Im wondering if you can set a fallback theme if GTK2 isnt supported. I dont know if that is the problem but it's the one thing I can think about. See screenshot. The synaptic manager is ugly as hell but the File Browser (cant spell nautellius) is awesome ;) .
It seems that the default theme doesnt have this problem, is it becauseit uses GTK1?
Anyhow, I would appreciate if someone could point me in the right direction or even tell me about a panther theme that works better.

---

### Post by grigpi on 2006-06-05
Try:
```
 sudo ln -s ~/.themes/ /root/.themes
```
and start synaptic.

---

### Post by DanielSwe on 2006-06-05
It worked perfectly! I didn't even think about the root account (which I selldom do in Ubuntu ](*,) ).
Thanks! :grin:

---

