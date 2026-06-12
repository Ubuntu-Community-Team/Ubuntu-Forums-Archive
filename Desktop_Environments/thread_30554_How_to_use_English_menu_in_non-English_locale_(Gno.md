---
title: "How to use English menu in non-English locale (Gnome)"
date: 2005-04-29
forum: Desktop Environments
---

### Post by jingjoeja on 2005-04-29
Hello,

Could anybody tell me how to config Gnome to use English menu and messages when I set system locale to non-English (e.g. Thai)?

I try setting LC_MESSAGES variable but it seems to have no effect (but setting LC_TIME to en_US made clock applet to display in English). Removing language pack made almost all program use English, except Gnome menu and launcher applet.

Thank you in advance,
Joe

---

### Post by strawberry on 2005-04-29
I suppose you configured one of english char-code tables with locales.
Gdm login screen choose 'languages', than one of english configuration (utf8 or posix). You can choose it only for one session or as default.
It worked for me, I hope it'll work for you too.

---

