---
title: "Automatic Login"
date: 2012-05-06
forum: Desktop Environments
---

### Post by linuxmatt7 on 2012-05-06
I was wondering on my Xubuntu 12.04 LTS Laptop how to enable automatic login. I forgot how I did it on my other Laptop running Xubuntu 6.06 LTS.

I can use the help fast.

---

### Post by Enigmapond on 2012-05-06
Just go to your User Accounts and initialize automatic login...

---

### Post by mips on 2012-05-06
```
sudo leafpad /etc/lightdm/lightdm.conf
```


Make sure the file looks like this:
> [SeatDefaults]
autologin-user=*<USERNAME>*
autologin-user-timeout=0
user-session=xubuntu
greeter-session=lightdm-gtk-greeter

---

### Post by linuxmatt7 on 2012-05-06
How would I configure in User Accounts I do not see it.

---

### Post by rubankumars on 2012-05-07
System>Administration>Login screen.
Then unlock.
enter password.
check login automatically radio button.

---

### Post by lightning slinger on 2012-05-07
Follow mips advice and see this page item#7

[http://xubuntu.org/news/faq-1204-precise/](http://xubuntu.org/news/faq-1204-precise/)

You have the option to set auto login during install!

---

