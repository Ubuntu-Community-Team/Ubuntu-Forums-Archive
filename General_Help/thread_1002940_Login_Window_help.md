---
title: "Login Window help"
date: 2008-12-05
forum: General Help
---

### Post by Havek on 2008-12-05
I recently installed a new login window and then moved the file to another folder.  Now when I turn on my computer it just sits there I believe trying to find that login window and never allows me to login.  I was wondering if anyone knew what file the login window information was stored in?  I found login.def but this seemed not to control the login window.  Thanks in advance

Havek

---

### Post by SomeGayDude on 2008-12-05
Are you asking about the styles and themes?
The themes directory is /usr/share/gdm/themes/

---

### Post by Havek on 2008-12-05
Yea I used the login window under administration to change it, now i am just looking for the file that the gui is modify, i will check in that dir and see whats in there.

---

### Post by Havek on 2008-12-05
Nope thats not it any other ideas?

---

### Post by SomeGayDude on 2008-12-05
The file that hold the data for stuff like what theme you are using for the login screen is /etc/gdm/gdm.conf-custom

---

