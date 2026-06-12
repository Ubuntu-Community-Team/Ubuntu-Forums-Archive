---
title: "xcompmgr fade?"
date: 2009-01-07
forum: General Help
---

### Post by dbbolton on 2009-01-07
I'm trying to get the fading effect to work with xcompmgr. Here is the command I used:

```
xcompmgr -c -t-5 -l-6 -r4.7 -o.65 -I 0.9 -O 0.9 -D 999
```However, I'm not seeing any fading. I'm using version 1.1.3+git20071107-0ubuntu1. Does anyone have a suggestion?

---

### Post by Forlong on 2009-01-07
The option for fade is -f
```
xcompmgr -c -f
```
works as expected here (looks rubbish, though).

---

