---
title: "TV-out killed X?"
date: 2008-05-17
forum: Desktop Environments
---

### Post by kobiyashi on 2008-05-17
I was fiddling with trying to get my TV-out on my laptop to work. At first it didn't work, and after restarting X, I was left with only 1024x768 as available resolution. I disabled the second screen (the TV) and rebooted. Now the laptop will only boot to console, and being a complete n00b at Linux in general, have no idea how to proceed. Trying to start Firefox gives me "no display specified" and startx gives me "caught signal 11." Ideas/help?

---

### Post by Xiong Chiamiov on 2008-05-18
First, try setting your xorg.conf back to the defaults:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
If that fails, you can try reinstalling X completely:
```

sudo aptitude purge xorg; sudo aptitude install xorg

```

---

