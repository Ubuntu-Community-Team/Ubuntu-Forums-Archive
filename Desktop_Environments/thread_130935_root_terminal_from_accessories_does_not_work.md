---
title: "root terminal from accessories does not work"
date: 2006-02-15
forum: Desktop Environments
---

### Post by Jeffj on 2006-02-15
When I select root login out of the accessories menu it sometimes works and sometimes does not. If I cut and paste the command from the menu edit into a user window it works as shown below. Why won't it work when I select it from the menu?
Could it be related to running the amd64 version?
-Jeff


jjm@moped:~$ sudo gnome-terminal --working-directory=%f
Password:

(gnome-terminal:1312): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:1312): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

---

