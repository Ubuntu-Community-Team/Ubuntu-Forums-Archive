---
title: "Black Screen after logging on Fresh build 8.10"
date: 2009-02-06
forum: Desktop Environments
---

### Post by caaron on 2009-02-06
After a fresh install of 8.10, I get the login screen.  Once I login I get a blank desktop with only the cursor, I can move it around but I can't click or anything else just move it around.  The only way out is the reset button or power button. Once the system boots back up I can hit ALT-F1 and get to the console where I can login just fine and move around as normal.  

Graphic Card = Intel Corporation 82845G (integrated):(

---

### Post by warp99 on 2009-02-06
Try making a new user account then add the same groups as your current user name, then login with that one. It may be something in your home user directory that causing the problem. Here's some howto info if you need it:

[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)
[http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/](http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/)

---

### Post by Yashiro on 2009-02-06
On your black desktop. Try opening a Terminal and entering metacity --replace. 
Alt+F2,xterm,metacity --replace.

---

