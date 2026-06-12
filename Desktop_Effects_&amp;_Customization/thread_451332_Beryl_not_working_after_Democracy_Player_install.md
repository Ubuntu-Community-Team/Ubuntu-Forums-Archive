---
title: "Beryl not working after Democracy Player install"
date: 2007-05-22
forum: Desktop Effects &amp; Customization
---

### Post by Peverel on 2007-05-22
Hi guys,

I just installed Democracy Player and after install (everything was fine) I played around and whoom the system crashed totally (I thought that won't happen to me again after switching to Linux :( ). Well, my Beryl-manager started up again but it doesn't work, it shows in the top panel but no effect, no window management nothing. 
I deinstalled Democracy again, but nothing changed.

Anybody got a solution to that one? Sorry I am new to Linux and after doing the google search  with no findings I am nearly helpless...

Thanks

P.S. 
Is there a option to restore settings before the Democracy install?

OK, I got it, sorry, I checked again on google and found a similar post...

Just changed window manager back from metacity to beryl....well, learning is a constant process... :)

---

### Post by Ateo on 2007-05-22
> **Peverel said:**
> and whoom the system crashed totally (I thought that won't happen to me again after switching to Linux :( ).

LOL. Um. What do you expect? Did you even bother to read that Beryl is ALPHA and just might crash your system? No? Hmm. Well, now you know. Whether you are new to linux or not does not exempt you from reading.

I would clear out Beryl settings from your gconf database:
```
$ gconf-tool2 --recursive-unset /apps/beryl
```

---

