---
title: "i have a nvidia 7100GS and i cannot get 1280x1024 to spawn."
date: 2007-05-23
forum: Desktop Effects &amp; Customization
---

### Post by kraymore on 2007-05-23
i have a nvidia 7100GS and i cannot get 1280x1024 to spawn.  the resolution selector doesn't even list it.  

thanks

---

### Post by renzokuken on 2007-05-23
firstly, do you know which video you are using? post your xorg.conf ( /etc/X11/xorg.conf ) if you are not sure how to find out. then......

go to the terminal and run

```
sudo dpkg-reconfigure xserver-xorg
```

leave everything as it is in the wizard until you get to the resolutions page, add in the resolutions you want then continue on leaving the rest as default.

press Ctrl+Alt+Backspace to restart the X-server and see if the new resolutions are available.

---

### Post by jonathanku on 2007-05-23
I have a nvidia 7300GT and also struggled to get 1280x1024.

I added lines to xorg.conf etc for the new resolution settings but got nowhere... **until** I found out the vsync/hsync figures for my monitor. Then it magically enabled 1280 x 1024.
Just a thought.

---

