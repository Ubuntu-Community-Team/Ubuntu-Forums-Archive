---
title: "Keeping the desktop in order"
date: 2006-12-15
forum: Desktop Environments
---

### Post by mgarcia-val on 2006-12-15
I've got Xubuntu 6.06 on a computer which is used by many, many students.

Is there a way in which I can disable access to configuration files, meaning basically, screen and desktop background configuration, menus layout, turning volume up and down, and so on? I'd like to disable it for users, allowing only the admin to make the necessary changes. I assume I should restrict permissions to some folder, but which one and how?

Thanks,
mgarcia-val

---

### Post by kalikiana on 2006-12-15
You might find this useful to protect the panel configuration:

_file:///usr/share/xfce4/doc/C/xfce4-panel.html#panel-kiosk_

Apart from that you might change the access rights of certain files located in ~/.config, to prevent users from changing options in certain applications.

---

