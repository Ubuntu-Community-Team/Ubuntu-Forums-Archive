---
title: "How to make GNOME displays a different language than the current locale?"
date: 2007-02-14
forum: Desktop Environments
---

### Post by pongtawat on 2007-02-14
Hello,

Could anybody please tell me how could I set GNOME on Edgy to display menu and messages in a language that is not my current locale? For example, I have to set my locale to Thai th_TH.UTF-8 for many programs to work properly, but I would like to menu to be in English (en_US.UTF-8). I have try to set LC_MESSAGES in many places (/etc/environment, /etc/default/locale,/etc/rc.local), but none seems to affect GNOME. So, please help :)

Thank you in advance,
Pongtawat

---

### Post by pongtawat on 2007-02-14
Ok, I finally found a way to do it (without understanding why).

I set

LANG=th_TH.UTF-8
LANGUAGE=en_US:en

in /etc/environment and /etc/default/locale and it works.
LANG is used as locale, while LANGUAGE is used to set GNOME UI language.

Pongtawat

---

