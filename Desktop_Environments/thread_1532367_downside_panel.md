---
title: "downside panel"
date: 2010-07-16
forum: Desktop Environments
---

### Post by kvtr on 2010-07-16
hi 

this is kvtr
i recently installed ubantu,
i had a small problem,there is no downside panel present in it . while when iam minimising websites i had to use alt+tab to maxmise them plz give some information to solve this problem


kvtr

---

### Post by llawwehttam on 2010-07-16
I presume you are using ubuntu with gnome.

Try going to Applications > Accessories > Terminal

and copy and paste this in:

```
gconftool --recursive-unset  /apps/panel 
killall gnome-panel
```your panels should then reset , and respawn.

Should fix most issues.

If not I will give you a different way of doing it.

---

### Post by kvtr on 2010-07-16
> **llawwehttam said:**
> I presume you are using ubuntu with gnome.

Try going to Applications > Accessories > Terminal

and copy and paste this in:

```
gconftool --recursive-unset  /apps/panel 
killall gnome-panel
```your panels should then reset , and respawn.

Should fix most issues.

If not I will give you a different way of doing it.

hey thanks dude my problem solved:D

---

