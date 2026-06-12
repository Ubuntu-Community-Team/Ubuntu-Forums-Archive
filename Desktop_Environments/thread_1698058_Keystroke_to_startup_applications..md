---
title: "Keystroke to startup applications."
date: 2011-03-01
forum: Desktop Environments
---

### Post by IWantFroyo on 2011-03-01
I followed the guides on the internet to put different wallpapers on each workspace, and pressed <ctrl><alt><f1> and <ctrl><alt><f7> to go to command line and refresh gnome. It worked, but now I have to hit those keys every time I start up. I need to set it to do this at startup. Can someone who knows how to do this please tell me how? Thanks.

---

### Post by IWantFroyo on 2011-03-01
Bump

---

### Post by Krytarik on 2011-03-01
First, please don't bump so fast, after 25 mins.

But since I looked up your case out of curiosity, I'll also give you an answer:

- install the package "lineakd", it's in the official repos.
- create a script with the following content and add it to "Startup Applications", you may need/want to modify the delays to fit the speed of your machine:
```
#!/bin/sh
sleep 13
xsendkeys Control_L+Alt_L+F1
sleep 2
xsendkeys Control_L+Alt_L+F8
```

---

