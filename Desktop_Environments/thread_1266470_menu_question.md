---
title: "menu question"
date: 2009-09-14
forum: Desktop Environments
---

### Post by new_tolinux on 2009-09-14
Hello,

Is it possible to edit the menu with the restart/shutdown/etc. options to prevent the usernames of other users to show up there.
At the moment, when user A is logged in, the menu is filled up by the accounts of other users and then follows the restart/shutdown/etc. options.

Greetz,
NewToLinux

---

### Post by Minsky on 2009-09-15
Open a terminal window and type:

```
gconf-editor
```

In the left-hand pane of the window that appears, goto
**apps > fast-user-switch-applet**, and in the large right-hand pane put a tick/check mark in the box next to the **show_active_users_only** key. You can also hide the Guest session option by removing the tick/check mark from the** show_guest_login** key.

---

### Post by new_tolinux on 2009-09-16
Thanks, that solved the "problem". :P

---

