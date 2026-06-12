---
title: "Cannot login (SessionManager destroyed)"
date: 2008-12-17
forum: Desktop Environments
---

### Post by erezz on 2008-12-17
Hi,

I'm trying to login from the 1st login screen in my kubuntu 8.10 (where you see a list of all users, and you need to supply a username + password). When I type my username+password, it accepts it but fails to log in. I get the same error every time (in ~/.xsession-errors):

Xsession: X session started for erez.zilber at Wed Dec 17 09:25:02 IST 2008
x-terminal-emulator: Fatal IO error: client killed
konsole(17430) Konsole::SessionManager::~SessionManager: Konsole SessionManager destroyed with sessions still alive 

If I open a shell (on tty1) and login, I can open an X session successfully by running 'startx -- :1'.

I'm sure that the problem is in my profile because other users can login successfully on my PC. Can anyone help?

Thanks,
Erez

---

### Post by prshah on 2008-12-17
> **erezz said:**
> 
x-terminal-emulator: Fatal IO error: client killed


Perhaps you need to run an fsck (disk check). From the terminal, give the command```
sudo touch /forcefsck
```

then reboot; it should run an automatic disk check.

---

### Post by erezz on 2008-12-17
> **prshah said:**
> Perhaps you need to run an fsck (disk check). From the terminal, give the command```
sudo touch /forcefsck
```

then reboot; it should run an automatic disk check.

I tried that. It looks like no errors were found, and when I try to login now, I get the exact same error.

Erez

---

