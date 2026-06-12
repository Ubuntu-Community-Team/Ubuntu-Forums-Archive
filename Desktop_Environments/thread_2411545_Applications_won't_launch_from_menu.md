---
title: "Applications won't launch from menu"
date: 2019-01-31
forum: Desktop Environments
---

### Post by mdshowman on 2019-01-31
Hello,

I have Ubuntu Mate 18.04, fully upgraded. I'm using this as an RDP session server. When I sign in as a user, I am unable to launch certain apps (in Games and Education categories) even though my path was set manually via .bashrc and .profile. The applications will run fine via the terminal, but these are grade school kids using the system, I don't want/need them going to the terminal to run applications.

How can I give users permissions to execute via the menu?

Result of echo $PATH:
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
```

I noticed that my .desktop entries in /usr/share/applications use relative paths rather than absolute, which makes me wonder if there is a symbolic link that I'm missing to make this function.

Thanks in advance!
-MD

---

