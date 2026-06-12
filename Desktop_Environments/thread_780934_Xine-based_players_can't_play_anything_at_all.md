---
title: "Xine-based players can't play anything at all"
date: 2008-05-03
forum: Desktop Environments
---

### Post by kuja on 2008-05-03
Thread title says all, In Kubuntu 8.04, I can't get any Xine based players (ie: amarok, kaffeine, kmplayer with xine engine, etc) to play anything at all, not Audio cds, flac, ogg, mp3, you name it. I'm not sure why it is, I've tried reinstalling any xine package I could think of, and the player packages as well. Any ideas anybody? I'll be back late tomorrow.

---

### Post by z0mbie on 2008-05-03
```
sudo aptituide kubuntu-restricted-extras
```

You can also try Dragon Player, it's a pure KDE4 multimedia application:
```
sudo aptitude install dragonplayer
```

Make sure your backports repositories are enabled.

---

### Post by kuja on 2008-05-04
Not relevant as I already have *both* of those installed.

---

### Post by Xiong Chiamiov on 2008-05-04
What about on a new user account (or after you've renamed your ~/.xine folder)?

---

### Post by kuja on 2008-05-04
Hmm, definitely had something to do with the configuration .... guess it had slipped my mind to do that at the time (I was pretty low on time anyway). I wonder which part of the conf did it ... I guess that'll be a good piece of busy-work for me to play with later.

---

