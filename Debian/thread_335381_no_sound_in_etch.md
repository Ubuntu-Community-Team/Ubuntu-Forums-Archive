---
title: "no sound in etch"
date: 2007-01-10
forum: Debian
---

### Post by unisol on 2007-01-10
i installed etch but i have no sound except for the speaker. i have  a soundblaster live anyone know why?

---

### Post by tturrisi on 2007-01-10
in a terminal do:
apt-get install alsa-base alsa-utils
then do:
alsaconf

---

### Post by marshcast on 2008-06-09
Thanks tturrisi  :)

---

