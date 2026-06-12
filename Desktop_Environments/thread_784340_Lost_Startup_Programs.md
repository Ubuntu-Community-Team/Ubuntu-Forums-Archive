---
title: "Lost Startup Programs"
date: 2008-05-06
forum: Desktop Environments
---

### Post by fmzw on 2008-05-06
When I opened "System->Preferences->Sessions", I mistakenly remove a startup item, something like "update user folder...". Now I want it back... but there is no revert...

Could anybody be kindly enough to post the original content of that item? That is, the Name, the Command, and the Comment of it. Thanks a lot!

---

### Post by bmac on 2008-05-06
Open Sessions:
system/preferences/sessions
startup tab

click on "Add"
Name: "User folder update"
Command: "Browse"
Select: "file system/user/bin/x11/xdg-user-dirs-gtk-update"
Comment: "Update common folders to match current locale"
Click on "OK"

This should add the start up preference to your session startup.

Hope this helped....:smile:

---

### Post by fmzw on 2008-05-06
Thank you very much!

---

