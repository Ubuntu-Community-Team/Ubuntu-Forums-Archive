---
title: "metacity takeover!!!!!!!"
date: 2005-08-22
forum: Desktop Environments
---

### Post by *nix_noob on 2005-08-22
i had just installed Mplayer (and some other stuff for it) and restarted...now when i login i see gnome keep loading "metacity window manager" and the window icon going all the way accross the gnome startup window...now i can only login in "gnome  failsafe"...how can i get the normal window manager back

PS: it only does this on my account  ](*,)

---

### Post by *nix_noob on 2005-08-22
heres a screenshot of gnome startup in normal mode...i wonder why its doing this?...

---

### Post by *nix_noob on 2005-08-22
I got it fixed!!

simply enter 

```
rm -rf .gnome && rm -rf .gnome2
```

in your command line....NOT AS ROOT

THIS WILL RESET GNOME TO DEFUALTS

---

### Post by KingBahamut on 2005-08-22
Be careful with that nasty rm <whatever> -fr command.....can be damaging.

---

