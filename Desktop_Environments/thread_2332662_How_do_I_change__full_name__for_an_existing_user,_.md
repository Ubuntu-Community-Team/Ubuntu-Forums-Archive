---
title: "How do I change  full name  for an existing user, and display full name in the panel?"
date: 2016-08-02
forum: Desktop Environments
---

### Post by noSelf on 2016-08-02
I know it was possible in pre-16.04 releases, but I can't remember. In 16.04.1 (Unity), the System Settings/User Accounts applet allows for entry of a full name when creating a new account, but doesn't seem to allow updating an existing account.

---

### Post by QDR06VV9 on 2016-08-02
See if this helps: [http://askubuntu.com/questions/34074/how-do-i-change-my-username](http://askubuntu.com/questions/34074/how-do-i-change-my-username)

---

### Post by deadflowr on 2016-08-02
In the user accounts page just click on the box in the main window area that contains the Full Name.
(it has an image box next to it and the Account Type is listed just below.)
Simply edit this and the Full Name will be changed.

To add the full name to the panel, though whether or not you like it either install dconf-editor or run this command
```
dconf write /apps/indicator-session/show-real-name-on-panel true

```
If you use dconf editor just follow the path. Which is simple enough; apps > indicator-session > show-real-name-on-panel > check or uncheck

---

### Post by CantankRus on 2016-08-04
There is also an option to "show name in panel" in User Accounts.

---

