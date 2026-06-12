---
title: "auth.log file"
date: 2009-03-20
forum: General Help
---

### Post by tienhn on 2009-03-20
Hi All,
I recently looked into the content of /var/log/auth.log files and found out that every time I mistyped my user name by entering the password. Then this password is logged in plain text in this log files.

Granted, this is my bad habbit by confusing between the log in prompt and the screen saver password prompt. So, if you check the log file, and if you are forgetful like I am, then you may see your password listed as a wrong user name in these log file.

Clear it with #cat /dev/null > /var/log/auth.log

Cheers,

---

