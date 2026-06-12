---
title: "Screwed up login with autologin"
date: 2009-04-20
forum: General Help
---

### Post by sonicb00m on 2009-04-20
I "stupidly" decided to enable autologin for gdm to see what would happen with an encrypted home directory. I soon regretted the decision because all I am welcomed with is a black screen with no possibility to restart the x server.

I stopped the loading of GDM and managed to start X but now i can't disable the autologin for GDM because it's not running.

I tried editing /etc/gdm/gdm.conf

and set autologin to false but it isn't working.

What do I need to edit or do to get my manual login working again without being presented with a black screen?

---

### Post by sonicb00m on 2009-04-20
It's ok, fixed it.

Right location, wrong file. Chose the custom one instead and it worked.

---

