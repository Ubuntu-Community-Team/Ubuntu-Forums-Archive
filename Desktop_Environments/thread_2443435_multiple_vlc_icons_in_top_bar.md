---
title: "multiple vlc icons in top bar"
date: 2020-05-15
forum: Desktop Environments
---

### Post by lee48 on 2020-05-15
Since upgrading to 20.04, I have multiple vlc icons that accumulate in the top bar every time I launch vlc and I can't get rid of them without rebooting. One piece of info said to go into preferences and check the box to allow only one instance of vlc. When I do that I can't launch vlc again after it has been launched one time. And the icon from the first launch remains in the top bar until I reboot. What else can I do?

---

### Post by monkeybrain20122 on 2020-05-15
How did you install vlc? Maybe you have a snap version and a deb version. Since you did an upgrade maybe some remnant of either one of them stays behind and when you installed vlc again you get duplicates. The software store gives you the snap and apt gives you a .deb.

---

### Post by philhughes on 2020-05-19
I get this if I close VLC with the X button. But if I close VLC using Quit from the appmenu, it terminates cleanly.

If you want to close it from the command line (having first checked what you will kill):

```
ps -eF | grep vlc
killall -s 9 vlc
```

---

