---
title: "Evolution not marking junk on its own"
date: 2005-10-23
forum: Desktop Environments
---

### Post by teevee on 2005-10-23
So I installed Spamassassin from universe some days ago, and edited the "ENABLED" variable in /etc/default/spamassassin to get something as fundamental as junk filtering working in Evolution (sigh, no further comment needed, right?). All relevant options within Evolution are activated too. Now when I mark something as junk in Evolution, a text appears in the status bar, saying the junk filter is learning, even "sa-learn --dump magic" confirms that it has learned. But Evolution is not checking for junk on its own, I always have to mark it manually. A search shows that lots of others seem to have the same problem, but no solution. Is junk filtering broken in Evolution and the final, stable Breezy release?

It's already ridiculously user-unfriendly to get so far in the first place (from the perspective of an average user, which is Ubuntu's main target group), but if even this workaround is broken, then that would be extremely poor.

---

### Post by ad noiseam on 2005-10-31
I have the same problem. It is already hard for new user to understand that they have to install Spamassassin *and* edit some configuration text deep before even having a possible spam filtering, but if this also doesn't work... :-/

---

### Post by djjuice on 2005-10-31
do you mind sharing what you edited to get spamassassin enabled

---

### Post by David Marrs on 2005-10-31
oh right, I need spamassassin installed. I wondered why nothing much was happening. :confused:

---

### Post by ad noiseam on 2005-10-31
[QUOTE=djjuice]do you mind sharing what you edited to get spamassassin enabled[/QUOTE]

Go to /etc/default/spamassassin and change:
ENABLE=0
to
Enable=1

Nicolas

---

