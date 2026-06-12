---
title: "Cannot enable desktop effects"
date: 2009-06-03
forum: Desktop Environments
---

### Post by The Toxic Mite on 2009-06-03
Hi all!

This may sound like a REALLY n00bish question, but I cannot enable desktop effects.

I know it's because my graphics card is blacklisted (Intel 965 I think it is :P) but here's the main thing:

I had a conversation with a few people on the #ubuntu-uk IRC channel on freenode.net, and I asked how I could "de-blacklist" the card in some way. This guy told me to do the following:

```
gedit ~/.config/compiz/compiz-manager
```

... and I had to add the following line to this file:

```
SKIP_CHECKS=yes
```

Everything worked fine from that.

BUT... I had to reinstall Ubuntu because it kept slowing down and all, and I couldn't be arsed to manually remove packages to speed up my system.

Now, with Ubuntu reinstalled, I tried to do what I described above, but now gedit is saying that compiz-manager. doesn't exist. It worked the last time, so I have no idea how it couldn't be working now.

I hope you can think of a solution to this :)

Any help will be appreciated :mrgreen:

-TTM-

---

### Post by Entropy_Sam on 2009-06-03
Hi there,
 
Take a look at the sticky thread on compiz in this very forum - at the top of the list there. That should be your first point of call for something like this. :-)
 
S

---

