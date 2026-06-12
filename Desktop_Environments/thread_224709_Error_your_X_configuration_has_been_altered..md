---
title: "Error: your X configuration has been altered."
date: 2006-07-28
forum: Desktop Environments
---

### Post by Scythe!? on 2006-07-28
I was trying to find out how to get ppracer to work. I found this nvidia driver config and when ran in the terminal, it says
```
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia
```

Anyone know how to fix it?

---

### Post by TheBlackNoodle on 2006-07-28
You're getting an error because the size of your xorg.conf changed, and the md5sum file (it's like a verifier of file integrity) wasn't updated with it.

So I'd try just doing what they say. Open a terminal, paste in this line:

sudo md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum

and hit enter. Then try running your config again.

---

### Post by CarlesOriol on 2006-07-28
Just read your question ... you'll see the answer.

---

