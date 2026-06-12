---
title: "Purge Korean from menus"
date: 2012-07-31
forum: Desktop Environments
---

### Post by ubuguitar on 2012-07-31
Ok, I am flummoxed. I attempted to install Korean language support and Korean keyboard support for an exchange student who was staying with me. It was unsuccessful while he was here, beyond a few items here and there the menus etc. all stayed in English and we were never able to get Korean characters from the keyboard. Now that he's gone back home, I tried to uninstall the Korean langauge pack, but it seems to have backfired and all my menus are now in Korean. Can someone tell me how to uninstall the Korean langauge pack through a terminal - I can't understand the menus to uninstall through the GUI!

Thanks!

---

### Post by ubuguitar on 2012-07-31
Well, some more googling gave me the solution. In case anyone else stumbles on this post, here it is:

From the terminal, type

sudo edit /etc/default/locale:

LANG="en_US"
LANGUAGE="en_US:en"
edit ~/.pam_environment:

LANG=en_US
LANGUAGE=en_US

---

