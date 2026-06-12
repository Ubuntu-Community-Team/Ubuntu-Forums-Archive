---
title: "Can't open Apps on first Login"
date: 2007-02-16
forum: Desktop Environments
---

### Post by timhaughton on 2007-02-16
I'm finding that when I first boot my machine and log in, I can't open any applications. If for example I try to open a console, it says opening console in the task bar at the bottom for a few seconds, then it disappears. To fix it, I have to log out and then back in again.

I dont't really know what other info to give.

Edgy
Beryl (although this happens with Beryl turned off)
Laptop. (Lenovo 3000 N100)

Cheers,

Tim

---

### Post by louis_nichols on 2007-02-16
Hm... I had a similar issue once. My problem was caused by messed file permissions in the home folder. I recommend you run these 2 commands:

```
sudo chown -R *username* /home/*username*
sudo chmod -R 755 /home/*username* 
```

Another idea is to troubleshoot this by starting applications directly from terminal and note the error it gives when crashing the application.

---

