---
title: "copy user settings"
date: 2010-08-27
forum: Desktop Environments
---

### Post by cccc on 2010-08-27
Hi

Howto copy a user with all personal settings like desktops icons, desktop background etc. under 10.04?
I'd like to create a new user with all settings from the existing user.

---

### Post by cccc on 2010-08-29
I've done the following and seems to work well:```

1.) # su -i
1.) # cp /etc/group /etc/group_save
2.) # adduser new_username
3.) # cp -a /home/old_username/* /home/new_username/
4.) # chown -R new_username:new_username /home/new_username
5.) in /etc/group find old_username and add new_username 

```

---

