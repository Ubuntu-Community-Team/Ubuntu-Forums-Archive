---
title: "How do I disbable the desktop by default in 8.04.1"
date: 2009-05-02
forum: General Help
---

### Post by ode on 2009-05-02
Hi,

I just installed Xubuntu desktop 8.04.1 LTS.

I have it booted and working but I wish to disable the desktop by default. I used to do this before with inittab but this is not there any more, I guess because of upstart.

Can someone please tell me how I can make this change please?

Thanks

---

### Post by geirha on 2009-05-02
You can stop xdm from being started automatically at boot with
```
sudo update-rc.d -f xdm remove
```

---

### Post by DeMus on 2009-05-02
> **ode said:**
> Hi,

I just installed Xubuntu desktop 8.04.1 LTS.

I have it booted and working but I wish to disable the desktop by default. I used to do this before with inittab but this is not there any more, I guess because of upstart.

Can someone please tell me how I can make this change please?

Thanks

Why do you want to do that? Any special reason?

---

### Post by Brandon Williams on 2009-05-02
The file /etc/X11/default-display-manager specifies the display manager that is allowed to run (gdm, xdm, kdm, etc.). If you just want a console login prompt, then you can open this file (e.g. sudo nano /etc/X11/default-display-manager) and remove all the content. If the file is empty, no display manager will start when you reboot.

---

### Post by ode on 2009-05-02
Hi, thanks for your replies.

geira:
'sudo update-rc.d -f xdm remove' didn't work for me. But since I was running xfce I figured I needed gdm instead of xdm. I made this substitution and it now boots without the desktop.

DeMus:
I installed this machine to use as a testing server mostly. But I wanted to install the desktop so I could use it occasionally if there was a problem with my main machine.

Brandon:
I read your reply after using the other method successfully. Thanks for replying though. I'll give your method a try if I need to do this again.

---

