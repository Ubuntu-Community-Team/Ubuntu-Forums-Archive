---
title: "Classic look of ubuntu-11.10 in root account"
date: 2011-11-26
forum: Desktop Environments
---

### Post by pavi_elex on 2011-11-26
How can I change Ubuntu 11.10 look into Gnome classic (no effects) in root account.I don't like unity at all.
I have tried 
apt-get install gnome-session-fallback
but it works only for users accounts not for root account.
Please suggest.

---

### Post by BC59 on 2011-11-26
The config file of Gnome theme is placed on Home directory. So when you log as root this config is out.

Maybe there is a way to do what you want, but it's not that easy.

---

### Post by coffeecat on 2011-11-26
Since [forum policy]("http://ubuntuforums.org/showthread.php?t=1486138") does not permit login as root to a GUI howtos, by extension support for configuring and using a root account GUI environment cannot be supported here.

@pavi_elex, by running a GUI as root you have severely compromised the security of your system. I suggest you become acquainted with the [Security Discussions forum]("http://ubuntuforums.org/forumdisplay.php?f=338"), and also read this excellent community documentation page:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

It tells you all you need to know about using root privileges relatively safely.

---

### Post by nothingspecial on 2011-11-26
> **coffeecat said:**
> Since [forum policy]("http://ubuntuforums.org/showthread.php?t=1486138") does not permit login as root to a GUI howtos, by extension support for configuring and using a root account GUI environment cannot be supported here.



For that reason this thread is closed.

---

