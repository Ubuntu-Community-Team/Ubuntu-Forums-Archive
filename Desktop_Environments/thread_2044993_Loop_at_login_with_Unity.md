---
title: "Loop at login with Unity"
date: 2012-08-20
forum: Desktop Environments
---

### Post by djibdjib on 2012-08-20
Hello, 

I've a loop at login under Ubuntu 12.04.
I don't remember doing anything special to get it...

When I enter my login and password, I get a  screen:
```
Stopping anachronistic cron
Stopping save kernel messages
Checking battery state
Stopping System V runlevel compatibility
```
And I come back to the login screen, undefinitely.
Note that I can always login in a terminal...

thank you for your help!

J-B

---

### Post by zombifier25 on 2012-08-21
Someone should really file a bug report, since for such an uncommon problem many people are having it.
Login in your terminal and type this command:
```
sudo chown yourusername:yourusername ~/.Xauthority 
```

---

