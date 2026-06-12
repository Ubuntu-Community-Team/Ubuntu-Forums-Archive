---
title: "Fast User Switching Xubuntu"
date: 2011-08-12
forum: Desktop Environments
---

### Post by King of Heart 4711 on 2011-08-12
How do I put an applet in my panel that will allow me to switch users, or throw me back to the GDM without logging me out.

---

### Post by XubuRoxMySox on 2011-08-12
You want to switch users without logging out? I don't think you can. One user logs out, the next logs on. No need to reboot in between users, just **[COLOR="Purple"]Menu -> log out[/COLOR]**. Then the login screen returns and the other user logs in. That's the only way I know.

If that isn't what you meant, please restate it. But I'm pretty sure logging out and in is the only way to switch users.

-Robin

---

### Post by King of Heart 4711 on 2011-08-12
> **dixiedancer said:**
> You want to switch users without logging out? I don't think you can. One user logs out, the next logs on. No need to reboot in between users, just **[COLOR="Purple"]Menu -> log out[/COLOR]**. Then the login screen returns and the other user logs in. That's the only way I know.

If that isn't what you meant, please restate it. But I'm pretty sure logging out and in is the only way to switch users.

-Robin

This must just be an xubuntu thing. I've been able to fast user switch (switching b/t users w/o logging out) with Ubuntu 11.04 and lower, Kubuntu 11.04 and lower, as well as other distros. 

It was just part of the session applet or logout/shutdown menu, with a button that stated 'switch user'.

---

### Post by Toz on 2011-08-12
There is an xfswitch-plugin available that will allow you to user switch in xubuntu on the fly:
```
sudo apt-get install xfswitch-plugin
```
or look for it in the Software Centre. Add it to your panel to use it.

---

