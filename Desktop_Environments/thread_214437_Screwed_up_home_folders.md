---
title: "Screwed up home folders"
date: 2006-07-12
forum: Desktop Environments
---

### Post by driesel on 2006-07-12
Hi,

When I was playing a bit in the GUI user administration of Ubuntu Dapper, I changed my home folder of user 'driesel' from '/home/driesel' to '/home'.
Which was a foolish thing to do really, since I'm not able to boot into Ubuntu anymore using any of the user accounts except for root (which I'm using now).

Is there any way to rest the home folder of 'driesel' to '/home/driesel' using the root account?
GUI user administration seems to be unavailable in root (it doesn't show up in System>admin)


greetings,
driesel

---

### Post by Paerez on 2006-07-12
from the console as root:
```
# usermod -d /home/driesel driesel
```

---

### Post by metalheart on 2006-07-12
Edit /etc/passwd file with text editor and change (i make an assumption here, it may look different!)
```
driesel:x:1000:1000:,,,:/home/:/bin/bash
```
to
```
driesel:x:1000:1000:,,,:/home/driesel:/bin/bash
```

---

