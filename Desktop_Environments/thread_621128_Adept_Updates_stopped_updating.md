---
title: "Adept Updates stopped updating"
date: 2007-11-23
forum: Desktop Environments
---

### Post by Sciamano on 2007-11-23
Hi,
I've just formatted my hard drive and installed Kubuntu Gutsy.
Of course Adept Updates immediately informed me of new updates. I launched the updates, it downloaded them correctly and then, after installing the first few updates, it stopped giving an error that said that it could not commit changes because this would have broken some packages.
I could not copy/paste the exact error, so I have to rely on my memory.

Anyway, the problem is that now, if I fetch for updates, it says there aren't any.
But the updates I had just downloaded were not installed due to the error, so shouldn't they still show up ad needed?

Please help. Thanks!

---

### Post by taurus on 2007-11-23
Close whatever window you have running the update.  Then, open a terminal and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Sciamano on 2007-11-26
This was the first thing I tried. No success.

---

