---
title: "How do I change the default DE for guest accounts?"
date: 2013-01-15
forum: Desktop Environments
---

### Post by Spr0k3t on 2013-01-15
I've installed Ubuntu 12.04 on a public use computer system and want to change the default environment over to Gnome without removing Unity.  Right now, every time the system is rebooted, logged out, it reverts to Unity... how do I change it so the default comes up Gnome?

On a side note, how do I include extensions and activate them on by default for the guest account?

---

### Post by TREESofRIGHTEOUSNESS on 2013-02-17
For the first part:
*Ctrl+Alt+T* will open a terminal
type in
```
gksu gedit /etc/lightdm/lightdm.conf
```
you'll be looking for the line
```
user-session=ubuntu
```
open your file manager and navigate to here:
**/usr/share/xsessions**
look for your fav session whether it is gnome shell or classic that you want (or your own variation with cario dock, etc..)

more info here:
[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

as for the second part... I am not quite sure what you mean by extensions... Are you talking about Gnome Shell extensions? (this seems the obvious answer... but obvious doesn't always mean correct)

---

