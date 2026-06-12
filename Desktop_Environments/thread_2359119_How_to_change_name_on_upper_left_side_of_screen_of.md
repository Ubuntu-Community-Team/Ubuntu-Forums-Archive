---
title: "How to change name on upper left side of screen of login"
date: 2017-04-20
forum: Desktop Environments
---

### Post by webmiester on 2017-04-20
Hi Everyone,

When I setup my first prototype with ubuntu, I named my computer "Prototype".  This name appears on the upper left hand side of the screen at login.  The thing is, I plan to simply clone the SD card of my ubuntu setup for the other units.  I want to change the name that appears on the upper lefthand part of the screen.  I already changed the hostname, in the users menu, but the Prototype name still appears.  How do I remove or change it?  Thanks so much.

---

### Post by Dennis N on 2017-04-20
I don't see a way to change the hostname of the computer you picked during installation from the Users dialog, but if the OS is recent enough, you should be able to use:

```
hostnamectl set-hostname *new-name*
```

---

### Post by ajgreeny on 2017-04-21
You can also manually edit the two files **/etc/hosts** and **/etc/hostname** and change the Prototype to whatever you want there.

I am assuming there has not been any change to an admin user's ability to do this with the introduction of systemd, but I have not needed to do this so it may be that this is no longer an option.

You will need to reboot for the change to take effect.

---

