---
title: "Disable Screen Lock"
date: 2006-06-21
forum: Desktop Environments
---

### Post by pat2man on 2006-06-21
Hi, I have a few laptops that automatcally log in so that users do not need a password. The only problem I am having is that when you close the lid, it locks the screen and asks for a password, is there a way to disable this? I already disabled the screensaver password...

---

### Post by 23meg on 2006-06-21
```
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_on_blank_screen false
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_use_screensaver_settings false
```should do it.

---

### Post by AndyC_772 on 2006-07-19
That works for me - thanks :)

---

### Post by joypunk on 2006-08-03
I used gconf-editor to set both of those settings to false, and now my screen won't even go to a Blank Screen when I close the lid (you can see the light from the screen peeking out from under the closed lid).

Power Manager is still set to "Blank Screen" when I close the lid. If I set "/app/gnome-power-manager/lock_on_blank_screen" to True, then the screen will go Blank (and lock the screen) when I shut the lid.

I want the screen to still go blank, but not to lock the system.

Any ideas?

---

### Post by jackmc on 2007-04-26
> **23meg said:**
> ```
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_on_blank_screen false
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_use_screensaver_settings false
```should do it.

Thanks :)

---

