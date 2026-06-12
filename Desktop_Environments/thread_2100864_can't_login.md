---
title: "can't login"
date: 2013-01-03
forum: Desktop Environments
---

### Post by joshp1 on 2013-01-03
I have only unity installed as my gui and all of a sudden my battery died now after battery charge my guis are missing how do I re-install them I can only get to the log in screen.  When I enter my password it goes right back to the log in screen

---

### Post by ryankidman on 2013-01-03
it seems its a virus problem

---

### Post by zombifier25 on 2013-01-03
> **ryankidman said:**
> it seems its a virus problem

I think not.

I have seen this problem too many times, and it's due to your sudden power off. At the login screen, press Ctrl + Alt + F1, log in, and type this command:
```
sudo chown yourusername:yourusername .Xauthority
```

then type "exit" to exit, and Ctrl + Alt + F7 to go back to your normal logging in screen.

---

### Post by joshp1 on 2013-01-03
didn't work thinks though for showing me how to get to the terminal.  I ran Unity --replace and got this

WARNING: no DISPLAY variable set, setting it to :0
Invalid MIT-MAGIC-COOKIE-1 keyInvalid MIT-MAGIC-COOKIE-1 keycompiz (core) - Fatal: Couldn't open display :0
unity-panel-service: no process found

---

### Post by zombifier25 on 2013-01-04
Run this command and post the output:
```
ll ~
```

---

