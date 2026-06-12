---
title: "gnome not loading"
date: 2009-03-03
forum: Desktop Environments
---

### Post by LogicBloke on 2009-03-03
Hello everyone,
i guess my problem is simple, while try to install gtk+, i had to install manually two other libraries, pango and atk, until now everything was relatively okay, next time i booted, there is no gui, just the background image, so i thought like my account lost rights, and i executed this command
```
sudo chown -R username:username /home/username
```

it just became worse, next time i booted, there is no background image, and the system goes automatically to console mode, asking me to login, with some errors, like "failed to load disk image from /dev/disk-[some hash] .." there was also something like "kinit" , when you i login it says the welcome message, but don't switch to gui mode. thanks in advance !

here are some of my log files, if you think that it will help.
[http://forum-hebergeur.freehostia.com/ubuntulogfiles](http://forum-hebergeur.freehostia.com/ubuntulogfiles)

---

### Post by Dar1us on 2009-03-03
try create another user, and login, if doesn't help, it seems like you have same library conflict. try reinstall gtk+ pango and atk. what say ~/.xsessions-error log file ?

---

### Post by LogicBloke on 2009-03-04
what is the path for this log you're telling me ? and I'll try to create a new user to see what it's gonna give me. but first it always asks me to login , there is an error just before it tells me to login, "kinit failed to boot ..." that i mentioned in the first post, and then after i log successfully, there are no errors, just the welcome messages !

---

### Post by LogicBloke on 2009-03-05
i created a new user and it's not working, since i get into the console mode, it sticks on it ! i created a user, i logged in with this new user, but it still in the console mode, is there any command i can run to launch the gui ?

---

### Post by LogicBloke on 2009-03-06
anybody here please ?

---

