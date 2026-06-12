---
title: "XFCE4 default settings?"
date: 2006-10-15
forum: Desktop Environments
---

### Post by .t. on 2006-10-15
On Ubuntu, if I install xfce4, I get the default settings from XUbuntu. If I don't install xubuntu-default-settings, I don't get any defaults. I just want the defaults that a vanilla installation of XFCE from their website provides. Is that too much to ask? If not, could you possibly point me in the right direction? Thanks!

---

### Post by taurus on 2006-10-15
Try removing ~/.config to see if it gives you what you want!!!

```
rm -rf ~/.config
```
Log out and back in again and see what happens...

---

### Post by .t. on 2006-10-15
Nope. It just uses the defaults found in /etc/xdg

---

