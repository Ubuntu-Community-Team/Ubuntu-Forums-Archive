---
title: "Missing min/max buttons. Can't move windows."
date: 2007-05-19
forum: Desktop Environments
---

### Post by mpc on 2007-05-19
I've come across a problem recently were all of a sudden it appears part of my Window manager has died or isn't starting. Gnome starts and I have the standard windowing environment but any apps I launch all start in the upper left corner of my screen, there is no bar to move them and therefore no min/max buttons.

Obviously, I've killed off or accidentally overwritten something key but I can't find anything in the syslog.  Any help?

---

### Post by aysiu on 2007-05-19
Are you able to open a terminal?

If so, try ```
metacity --replace &
```

---

### Post by mpc on 2007-05-19
> **aysiu said:**
> Are you able to open a terminal?

If so, try ```
metacity --replace &
```

I'll give that a try. I can open a terminal window but not at the machine today.  Thanks for the quick reply.

---

### Post by kikdadog on 2007-05-19
Had the same problem after I tried the desktop effects, your fix worked for me, Thank you!!!!!!!!!!

---

### Post by mpc on 2007-05-21
> **aysiu said:**
> Are you able to open a terminal?

If so, try ```
metacity --replace &
```


OK, that worked and I've narrowed down what caused the problem. The latest metacity path/upgrade was the cause.  I had the exact same thing happen on my home system and the same fix worked.  Only problem is on the home system (using a NVidia 5700) I can no longer set resolutions above 640x480 since the latest "upgrades".  I'm thinking the last batch of patches/upgrades has some issues to work out.

---

