---
title: "Debian 8 SU Delay Issue"
date: 2015-06-01
forum: Debian
---

### Post by Xaotique on 2015-06-01
After having Debian 8 installed with Gnome, I decided to remove Gnome and go with Xfce.  I assume completely removing Gnome has something to do with this, but "su" has been very slow since.  From a little Google searching, it seems to be a delay timeout for finding your key?  Creating an .xauth/export file as suggested in many places did nothing to help this.

```
su
Password: 
(long wait - about 20 or 30 seconds)
```

While ..

```
sudo xfce4-terminal
(log in)
(instant results with a terminal popping up as SU)
```

So, does anyone have any idea why "su" would be so slow, but "sudo" is perfectly fine?

# Edit
This seems to be an issue with slow logging in as any user.  Well, at least "root" and my regular user.  So, maybe that's the difference between "su" and "sudo" acting up, but I still have no idea why it's so slow.

---

