---
title: "Login screen resets after password entered"
date: 2010-04-06
forum: Desktop Environments
---

### Post by SGC622 on 2010-04-06
ok i have kubuntu 9.10 installed on my computer and i was using kiso which i had to run as root, simultaneously running acidrip ripping two dvds aswell. all of a sudden my desktop goes blank and only the windows im using at the time remain. i still have alt tab function to switch between my running applications, but i go to hit ctrl at delete. and it goes to the login window. so figuring i reset something or something crashed, i retyped my password and pressed enter, and the screen went black like it was going to start kde but reset back to the login screen. so i restarted, shutdown and waited a minute, and the same thing, anyone have a fix for this?  so anyway i clicked on the menu on the login screen and clicked on console login, and it let me login im not very good with terminal so once im logged in i have no idea what to do in console login.

i just found on another forum im reading, if there is a lack of space, that could also be why im experiencing this, if thats the case how do i delete a folder that i think could fix it with console login?

---

### Post by micio on 2010-04-08
cd /path/where/you/want/go
rm /file/in/path/ to delete files

you can try also to log in with an other user name or you can also rename your home folder from /home/user to /home/user.old and log in back again (it should create a new files/folders hyerarchy)

To create a new usersname you must issue this command 

```
sudo adduser username
```

Micio

---

