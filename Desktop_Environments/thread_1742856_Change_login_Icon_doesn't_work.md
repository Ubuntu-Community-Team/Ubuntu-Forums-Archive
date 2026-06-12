---
title: "Change login Icon doesn't work"
date: 2011-04-29
forum: Desktop Environments
---

### Post by hashcode on 2011-04-29
Hi, I try to change my login icon to another with ubuntu tweak, but it doesn't work after logout.

- ubuntu tweak shows correct icon but doesn't use it
- icon path is correct
- icon size is correct

I have been using Macbuntu and old icon, that I always see, is apple logo.
Is there other way to change it?

I'm now on Natty with Unity.

---

### Post by Copper Bezel on 2011-04-29
If Macbuntu changed the icon theme of the login screen, then Ubuntu Tweak can't change the icon itself - it makes some assumptions based on the LoginIcons theme.

To change the login screen's icon theme back to the default so that Ubuntu Tweak can make the change to it you want, see [here]("http://ubuntuforums.org/showthread.php?t=1726016").

---

### Post by hashcode on 2011-04-29
Didn't work.

I located macbuntu apple icon and deleted it manually, so now it only shows black box with red circle (like emblem of "hey I am missing something here").

---

### Post by Krytarik on 2011-04-29
> **hashcode said:**
> 
I located macbuntu apple icon and deleted it manually
Where was it?

Also, try running this:
```
sudo rm -rf /var/lib/gdm/.icons
```And post the outputs of these:
```

sudo -u gdm gconftool-2 --get /desktop/gnome/interface/icon_theme
sudo -u gdm gconftool-2 --get /apps/gdm/simple-greeter/logo_icon_name
```

---

### Post by hashcode on 2011-04-30
it was applelogo-black.svg that I  deleted in /usr/share/icons

so I used another icon I want, named it applelogo-black.svg and copied there :D

thanks :)

---

