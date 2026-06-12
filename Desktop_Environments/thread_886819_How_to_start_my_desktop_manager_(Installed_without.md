---
title: "How to start my desktop manager (Installed without one)"
date: 2008-08-11
forum: Desktop Environments
---

### Post by blazemore on 2008-08-11
I installed Debian without a desktop environment.

I then downloaded, compiled, and installed Openbox.

My question is how do I run it? StartX doesn't work, and I don't even know if X is installed.

Might be a stupid question but can anyone help?

---

### Post by sebbss on 2008-08-11
What does it tell you when you type startx?

---

### Post by eriqjaffe on 2008-08-11
> **blazemore said:**
> My question is how do I run it? StartX doesn't work, and I don't even know if X is installed.If you installed a command-line system and didn't explicitly install xorg through apt-get, then it's not installed.

```
sudo apt-get install xorg
sudo dpkg-reconfigure xserver-xorg
startx
```

...**should **sort you out.

---

