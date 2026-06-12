---
title: "how to reallocate VRAM ??"
date: 2005-09-12
forum: Desktop Environments
---

### Post by necco on 2005-09-12
hello everybody.  i'm testing hoary. i'd like to reallocate video ram manually. with other debian based releases (sarge/knoppix/kanotix) i go through a root terminal and use dpkg-reconfigure xserver-xfree86. this package do not seem to be available with hoary. any clue ? i presume the graphic engine is dealt through another package i am not aware of... (resolution is ok on a nm256 2,5 MbVRAM but refresh does not want to take over 60Hz. it should reach 75Hz for a 1024resolution) thanks for reading... and regards !!

---

### Post by arnieboy on 2005-09-13
[QUOTE=necco]hello everybody.  i'm testing hoary. i'd like to reallocate video ram manually. with other debian based releases (sarge/knoppix/kanotix) i go through a root terminal and use dpkg-reconfigure xserver-xfree86. this package do not seem to be available with hoary. any clue ? i presume the graphic engine is dealt through another package i am not aware of... (resolution is ok on a nm256 2,5 MbVRAM but refresh does not want to take over 60Hz. it should reach 75Hz for a 1024resolution) thanks for reading... and regards !![/QUOTE]
do a:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by necco on 2005-09-14
thanks for the hint but still it does not wanna understand anything higher than a 60 refresh.... :( i'll try entering vertical and horizontal rates manually but i doubt it helps...

---

