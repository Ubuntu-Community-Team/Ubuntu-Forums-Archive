---
title: "How do I log in to the gnome gui as my root user?"
date: 2006-02-25
forum: Desktop Environments
---

### Post by YellowHat on 2006-02-25
It tells me the administrator is not supposed to log in there. I need to run easy ubuntu but I have to run it as my root user. Seriously, come on help.

---

### Post by shams2 on 2006-02-25
login as root is desabled in the ubuntu, you can simply change to root in the shell wiht:
sudo su
any graphical tool need root Privilege will ask for your password.

---

### Post by Sirin on 2006-02-25
There is a bug with easyUbuntu that it won't accept your password, but it can be bypassed using

```

cd {YOUR EASYUBUNTU DIRECTORY HERE}
sudo ./easyubuntu.py

```

but if you ABSOLUTELY NEED to login as root (although it's a security risk), take a look at [https://wiki.ubuntu.com/RootSudo?action=show&redirect=EnableRootLogin](https://wiki.ubuntu.com/RootSudo?action=show&redirect=EnableRootLogin) :)

---

### Post by dcstar on 2006-02-25
[QUOTE=YellowHat]It tells me the administrator is not supposed to log in there. I need to run easy ubuntu but I have to run it as my root user. Seriously, come on help.[/QUOTE]
System-Administration-Login Screen Setup-Security-Allow root etc.

---

