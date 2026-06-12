---
title: "Custom Login Screen"
date: 2009-09-12
forum: Desktop Environments
---

### Post by kiwited on 2009-09-12
I have a public computer which runs Xubuntu 8.10. Although it is set to automatically log in guests when it is booted, it is common for guests to log out when they are finished. The next user is then faced with a login screen requiring username and password. The auto login does not seem to work in this situation.

It is my wish to modify the login screen to state the required username and password on the screen. Where is the image file for the login screen and can it be modified?

Thanks,

Theo

---

### Post by yabbadabbadont on 2009-09-12
/usr/share/gdm/themes/<insert your gdm theme name here>

There is an xml file that defines the theme.  In that file, there will most likely be a background image defined.  Modify that image file to include the information that you desire.

---

### Post by kiwited on 2009-09-13
Many thanks. It is so easy when you know where to look.

Theo

---

### Post by mcduck on 2009-09-13
> **kiwited said:**
> I have a public computer which runs Xubuntu 8.10. Although it is set to automatically log in guests when it is booted, it is common for guests to log out when they are finished. The next user is then faced with a login screen requiring username and password. The auto login does not seem to work in this situation.

It is my wish to modify the login screen to state the required username and password on the screen. Where is the image file for the login screen and can it be modified?

Thanks,

Theo

How about using timed login instead of automatic? That will log the guest user in after a set time and works even after logging out..

---

