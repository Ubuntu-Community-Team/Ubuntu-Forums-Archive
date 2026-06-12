---
title: "Question about the resolution"
date: 2005-08-08
forum: Desktop Environments
---

### Post by glowstick on 2005-08-08
How come I can use 1280 x 1024 in Windows XP but in Ubuntu I can only select up to 1024 x 768?

---

### Post by iH8forcedRegistration on 2005-08-08
[QUOTE=glowstick]How come I can use 1280 x 1024 in Windows XP but in Ubuntu I can only select up to 1024 x 768?[/QUOTE]
 Debian/ubuntu's default x11 settings would seem to limit the resolution to 1024x768.

try
```
sudo dpkg-reconfigure xserver-xorg
```

---

