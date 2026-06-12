---
title: "Ubuntu GNOME SHELL"
date: 2013-09-12
forum: Desktop Environments
---

### Post by narendra4 on 2013-09-12
Hello,
       I have a dell Inspiron 1545.Ubuntu 12.04 and now I have installed Ubutu GNOME SHELL and Extension, But How can I use That? I dont Seen any chage in graphics or the desktop environment..please help

---

### Post by ajgreeny on 2013-09-12
You have to make the choice at login using the small wheel like icon in the login box, though I am not sure whether you can have both unity and gnome shell on the same user's configuration or same OS; I seem to remember hearing about some conflict or other, though I may be wrong.

If it is possible:-
**Ubuntu** at login will give you unity,
**Gnome** (or something similar) will give you gnome shell.

---

### Post by cmcanulty on 2013-09-12
if you have auto login log out first to see the options then you can pick and reset to auto login and system will remember your choice

---

### Post by kurt18947 on 2013-09-12
> **ajgreeny said:**
> You have to make the choice at login using the small wheel like icon in the login box, though I am not sure whether you can have both unity and gnome shell on the same user's configuration or same OS; I seem to remember hearing about some conflict or other, though I may be wrong.

If it is possible:-
**Ubuntu** at login will give you unity,
**Gnome** (or something similar) will give you gnome shell.

Exactly.  I'm doing the same thing.  I install the default Ubuntu then add  gnome-shell and maybe Xfce4 and/or LXDE (NOT the desktops, I like the default Ubuntu apps for the most part).  There may be some small confusion but nothing significant.

---

### Post by 2Stoned on 2013-09-12
Try this:    ```
 [COLOR=#000000][FONT=Calibri][SIZE=2]sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-shell [/SIZE][/FONT][/COLOR] 


```

Logout and login again. Or reboot the syetem for the best performance

---

