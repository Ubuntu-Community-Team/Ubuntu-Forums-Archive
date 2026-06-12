---
title: "Esperanto circumflexes (supersigno) option in Xubuntu"
date: 2013-11-13
forum: Desktop Environments
---

### Post by dohnp5a1 on 2013-11-13
In Ubuntu, it was very easy to write special Esperanto characters by electing the option "add Esperanto circumflexes (supersigno)" in the keyboard settings. I have beend forced to migrate to Xubuntu and there is no such option in the keyboard setting. How could I sort this problem out?

---

### Post by rodrigog83 on 2013-11-26
In my case I solved this running the following command (you might want to add a startup script for it):

```
setxkbmap -layout "**latam**" -variant "" -option "lv3:lwin_switch" -option "esperanto:qwerty"
```

You must change "latam" (Latin American) to your keyboard layout. But still would be nice to have the option in the keyboard settings.

> **dohnp5a1 said:**
> In Ubuntu, it was very easy to write special Esperanto characters by electing the option "add Esperanto circumflexes (supersigno)" in the keyboard settings. I have beend forced to migrate to Xubuntu and there is no such option in the keyboard setting. How could I sort this problem out?

---

