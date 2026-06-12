---
title: "I Nees To Change"
date: 2008-06-13
forum: Desktop Environments
---

### Post by eshuaipi on 2008-06-13
HELLO EVERY BODY. i NEED SOME HELP.

I installed on my UBUNTU the KDE desktop interface to check it how it looks, but I realised that GNOME is much better for me, so I turned back to gnome. But I got a problem. My boot loader now it apears like KUBUNTU when I turn on and off my system. I really do not like it because I prefere better the UBUNTU orange colour.

HOW CAN I CHANGE BACK THE BOOT LOADER TO UBUNTU SCREEN???

---

### Post by overdrank on 2008-06-13
> **eshuaipi said:**
> HELLO EVERY BODY. i NEED SOME HELP.

I installed on my UBUNTU the KDE desktop interface to check it how it looks, but I realised that GNOME is much better for me, so I turned back to gnome. But I got a problem. My boot loader now it apears like KUBUNTU when I turn on and off my system. I really do not like it because I prefere better the UBUNTU orange colour.

HOW CAN I CHANGE BACK THE BOOT LOADER TO UBUNTU SCREEN???

Hi and welcome, you can go to system, administration, login window. Select the local tab and you can change it there. :)

---

### Post by argail1980 on 2008-06-13
try on the console

```
dpkg-reconfigure gdm
```

that should ask, if you want gdm to be the default display manager. answer "yes" to that. 

The brute force method is to remove the script kdm from /etc/init.d/, **but you'd better not do that**, because I have no idea what exactly will happen.

---

