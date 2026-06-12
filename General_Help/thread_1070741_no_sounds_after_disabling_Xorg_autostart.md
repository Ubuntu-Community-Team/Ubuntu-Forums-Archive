---
title: "no sounds after disabling Xorg autostart"
date: 2009-02-15
forum: General Help
---

### Post by mummim on 2009-02-15
I have got no sound after disabling Xorg autostart by the command:
```
sudo update-rc.d -f gdm remove
```

The sound work normaly with vlc in console mode.

---

### Post by mummim on 2009-02-15
I have firgured out the reason. Somehow my user's permisson was changed after disabling Xorg (or smoething else). I loged as root and changed the permission, everything is perfect again.
Thanks.

---

