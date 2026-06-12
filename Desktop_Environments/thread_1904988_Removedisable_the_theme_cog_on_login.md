---
title: "Remove/disable the theme cog on login"
date: 2012-01-05
forum: Desktop Environments
---

### Post by H3110 on 2012-01-05
Hi All,

I have Ubuntu 11.10, with Gnome 3.

I recently edited the lightdm.conf file to replace my background image on the logon workspace, I then disabled the guest-login leaving me with the "Username" login box and the "Other..." logon box.

Replaced background image via:
```
$ sudo gedit /etc/lightdm/unity-greeter.conf
```

Disabled guest logon via:
```
$ sudo gedit /etc/lightdm/lightdm.conf
```
```
allow-guest=false
```

I would like to somehow disable, remove otherwise hide the cog which is displayed on the top-right corner of the user login box (where the username is shown and presented with a password field only).

I do not want the theme to be changed or switched by me or any other user (it my personal laptop with other users for friends to use occasionally).


Thanks for any help in advance.

---

