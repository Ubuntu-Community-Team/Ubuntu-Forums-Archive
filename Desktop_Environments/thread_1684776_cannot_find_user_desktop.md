---
title: "cannot find user desktop"
date: 2011-02-09
forum: Desktop Environments
---

### Post by ernst.tamsen on 2011-02-09
After a total hangup while downloading a largeish jpg, my desktop doesnt show any icons and both monitors show the same. Other users have same problem. When I try to reactivate the two-monitor setting, I get the message: "The monitor configuration could not be saved. Error executing command as anther user. no authentication agent found" (or words to that effect - my messages are in german). the thing that puzzles me is that the correct desktop background is shown - so not all settings are lost.
can anyone help?
is this a common fault?
or whewe are these configurations stored?

tia

ernst

---

### Post by Krytarik on 2011-02-10
That's just a wild guess, but check who is the owner of "~/.ICEauthority", it should be yourself, otherwise change it.
```
ls -al ~/.ICEauthority
``````
sudo chown USERNAME.USERNAME ~/.ICEauthority
```

---

