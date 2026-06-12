---
title: "Nautilus error - undefined symbol"
date: 2008-05-08
forum: Desktop Environments
---

### Post by antisho on 2008-05-08
When I try starting nautilus I get the following error:

```
$ nautilus
nautilus: symbol lookup error: nautilus: undefined symbol: eel_art_irect_empty

```

I have tried various combinations of restarting and reinstalling libeel* and nautilus, but to no avail. Can anyone help?

---

### Post by haytona on 2008-05-20
See here: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/218321/comments/4](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/218321/comments/4)

libeel2 was the culprit in my case.

---

