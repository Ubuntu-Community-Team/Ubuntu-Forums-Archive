---
title: "Possible to enable VNC access to Ubuntu with only SSH access?"
date: 2006-09-15
forum: Desktop Environments
---

### Post by chapterthree on 2006-09-15
Hi Guys,

I have a situation where I only have SSH access to my Ubuntu box right now.  I need to 'enable' VNC access on my Ubuntu box.  Please note the Ubuntu box is booted up to the GUI login screen, I just don't have the resources to plugin a keyboard, mouse and monitor right now.

Is it possible to enable Remote Desktop access if I only have access to the Ubuntu box via SSH?

Thanks

---

### Post by sharky44 on 2006-09-15
I've never used VNC before, but you /should/ be able to log in to a terminal through ssh:
```
ssh username@host
```
At that point, you should be able to install/configure/start VNC by using the command line and apt-getting the appropriate packages.  As I said, I've never used VNC, but you should be able to do something like /etc/init.d/vnc start (or whatever startup script your VNC server places there).  

I hope that wasn't too elementary, and my intention is not to insult anyone's intelligence, but this is what I would try.  If you have a more specific issue, post it here and we may be able to help you out.

---

