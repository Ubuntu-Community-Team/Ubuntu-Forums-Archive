---
title: "OSS install (not emulated)"
date: 2005-09-29
forum: Desktop Environments
---

### Post by lgvier on 2005-09-29
Hi,

How can I use the old OSS drivers?
My audio card is a Maestro 1964 (on alsa)
I use some applications that not work using ALSA.

thanks in advance :)

---

### Post by mtron on 2005-09-29
install the ALSA OSS-compatibility application wrapper. It does exactly what you need. 

sudo apt-get install alsa-oss

and swith the sound system to alsa  (System - Pref -Multimedia System Selector) and disable the Sound Server on Startup (System - Pref - Sound)

---

### Post by lgvier on 2005-09-30
Wow! 
It just works!! :D 
Thanks!

---

### Post by mtron on 2005-10-01
welcome! ;-)

---

