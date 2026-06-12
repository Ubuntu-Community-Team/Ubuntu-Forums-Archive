---
title: "How to install a new monitor?"
date: 2006-01-17
forum: General Help
---

### Post by blackant on 2006-01-17
Is there anyway to redetect my new monitor?
I was using a CRT then, but switch to a 17" lcd now.

But the settings is still using the old crt...:confused:

---

### Post by Gustav on 2006-01-17
type this in the terminal:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by blackant on 2006-01-18
[QUOTE=Gustav]type this in the terminal:
```
sudo dpkg-reconfigure xserver-xorg
```[/QUOTE]
Thanks.
But how come inside my nividia settins, it still shows a crt-0?

---

