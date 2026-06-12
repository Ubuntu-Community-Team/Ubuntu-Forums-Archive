---
title: "autologin config file"
date: 2012-02-14
forum: Desktop Environments
---

### Post by cccc on 2012-02-14
hi

Where is the autologin config file in XFCE?

---

### Post by ankspo71 on 2012-02-15
In Xubuntu 11.10 which uses lightdm for a display manager, the file you are looking for should be: /etc/lightdm/lightdm.conf

Here is what mine looks like:
> 

[SeatDefaults]
autologin-guest=false
autologin-user=ankspo71
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=xubuntu
greeter-session=lightdm-gtk-greeter


Be sure to replace my name with your name. This might be important: My autologin was configured for me during installation, so I don't know if there would be any other additional steps needed to make autologin work properly.

Hope this helps.

PS: If you are using an another version of XFCE (or Xubuntu), more specifically one that uses XDM as a display manager, then as far as I know XDM doesn't support autologin.

---

### Post by cccc on 2012-03-04
Thx a lot!

---

