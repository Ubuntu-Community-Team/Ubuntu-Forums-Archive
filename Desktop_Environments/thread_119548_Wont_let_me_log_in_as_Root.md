---
title: "Wont let me log in as Root"
date: 2006-01-19
forum: Desktop Environments
---

### Post by sooperspook on 2006-01-19
During the installation it gave me the option of creating a user name etc but i decided not to, thinking i could create one after. I didn't realize that it wouldnt let me log in as Root tho. Any suggestions?

---

### Post by darth_vector on 2006-01-19
boot into safe mode (hit ESC on startup to get the GRUB menu, and select single user mode/safe mode/whatever its called). you will get a root shell. use the adduser command to create a new user (ie. you) and make sure you add yourself to the sudoers file. a line like```
username ALL=(ALL)ALL
```should do it.

restart the machine with```
shutdown -r now
```

post back if you have any problems. we will help you out.

---

