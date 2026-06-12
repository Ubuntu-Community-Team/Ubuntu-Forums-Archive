---
title: "Keyboard layout switching problem"
date: 2006-02-19
forum: Desktop Environments
---

### Post by Drovosek on 2006-02-19
Hello, all!
I got a problem with the new installation of Ubuntu 5.10 (never had it in the past with Debian ones).
The normal keyboard switching works only with right alt-shift - then the layouts are sequentialy switched and wrapped around.
When I use left alt_shift, the layouts are only switched back to the first one and do not wrap around.
I have three layouts defined - us,ru and he. So, for each right alt-shift I got us->ru->he->us->ru etc.
If the current layout is "us", then left alt-Shift does nothing. If the current layout is he, then pressing left alt-shift switches it back to "ru", then to "us" and stucked there.
The xorg.conf has nothing special:
     Option "XkbLayout"    "us,ru,he"
     Option "XkbOptions"   "grp:alt_shift_toggle,grp_led:scroll"
     Option "XkbVariant"    ",phonetic,lyx"

What's wrong?

---

