---
title: "square notificataions ?"
date: 2008-06-03
forum: Desktop Environments
---

### Post by iamnotthemessiah on 2008-06-03
i hate the rounded bubble notifications in hardy. soem releases ago they were square. is there a way to configure them to get them square again ?

---

### Post by mcduck on 2008-06-03
No problem, that's easily fixed.. :D

1. Press Alt-F2 and run "gconf-editor"

2. Browse to /apps/notification-daemon/

3. Change the value of the "theme"-key from "ubuntu" to "normal".

Now you get Gnome's default square notifications.

---

