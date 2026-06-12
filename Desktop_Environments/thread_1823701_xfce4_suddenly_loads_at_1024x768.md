---
title: "xfce4 suddenly loads at 1024x768"
date: 2011-08-12
forum: Desktop Environments
---

### Post by wbuntu on 2011-08-12
Everytime i boot i must execute "xrandr -s "1280x1024" to fix,
How can i keep it "1280x1024" forever.
Thanks.

---

### Post by madjr on 2011-08-12
> **wbuntu said:**
> Everytime i boot i must execute "xrandr -s "1280x1024" to fix,
How can i keep it "1280x1024" forever.
Thanks.

do you have more than 1 monitor or another desktop environment installed like gnome or kde?

---

### Post by Toz on 2011-08-12
> **wbuntu said:**
> Everytime i boot i must execute "xrandr -s "1280x1024" to fix,
How can i keep it "1280x1024" forever.
Thanks.

According to: [https://wiki.ubuntu.com/X/Config/Resolution#Setting_xrandr_changes_persistently]("https://wiki.ubuntu.com/X/Config/Resolution#Setting_xrandr_changes_persistently"), the place to put them is in your **~/.xprofile** file, or **/etc/gdm/Init/Default** before the command:
> /sbin/initctl -q emit login-session-start DISPLAY_MANAGER=gdm

---

