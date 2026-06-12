---
title: "X-sever fails to load"
date: 2005-11-28
forum: Desktop Environments
---

### Post by Confused Fishcake on 2005-11-28
I have a triple-boot pc (Ubuntu,XP,XP) but for some reason, when I started Ubuntu just now, I get a xsever error, saying it has failed to load. I can still login and get a terminal, but nothing else. Is there any way I can download a clean version of the x server? I can get connected to the internet, but not load firefox (I can apt-get) Please help, as I really need Ubuntu working.

---

### Post by Kyral on 2005-11-28
First try this

```
sudo dpkg-reconfigure xserver-xorg
```

---

