---
title: "Send message to notification area."
date: 2008-11-09
forum: Desktop Environments
---

### Post by dlublink on 2008-11-09
Hello,

I wrote a bash script that is launched by udev when I plug certain hardware in. I want the bash script to notify the user, logged into gnome, what is happening. 

Can I pipe the output to a command so that it displays it to the user?

Thanks,

David

---

### Post by f37u5g0d on 2009-05-26
run notify-send "Done!"

---

### Post by mcduck on 2009-05-26
..or use Zenity. It can do many kinds of dialogs, popup windows and notifications.

---

