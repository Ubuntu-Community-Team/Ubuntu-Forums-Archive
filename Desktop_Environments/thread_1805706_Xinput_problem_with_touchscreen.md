---
title: "Xinput problem with touchscreen"
date: 2011-07-16
forum: Desktop Environments
---

### Post by JBtje on 2011-07-16
Greetingz,
 
After searching whole day, I figured out how to configure the Xinput, so that the touchscreen actually works correctly (and is not being invertes now swapped anymore).
 
Thought, when I logged out and in again, the config is gone :|
 
In order to keep the config, i need to load the config each time the server starts. my question is: where would i need to place the file!?
 
The content of the file is:
 
```
xinput set-prop 8 281 1 x
xinput set-prop 8 279 1 0
xinput set-prop 8 280 100 4000 200 3900
```
 
Beside that i dont really know where to place it, I also go the problem that is needs to work when the login screen appears...
 
Who can help me with this?
 
Thank you!
JB

---

