---
title: "error loading gui"
date: 2008-08-19
forum: Desktop Environments
---

### Post by ravi25k on 2008-08-19
i come to login schreen and when i enter username and password i get a meggage box saying i have been logged out in 10 sec with a error message attached to it 

/etc/gdm/permission/default:registering your section with wtmp and utmp
/etc/gdm/PreSession/Default:running :/user/bin/sessreg -a -w /var/log/wtmp -u/var/run/utmp -x "/var/lib/gdm/:0.xservers "-h " "-l " " :0" "rav"
/etc/gdm/xsession:begining session setup
/user/bin/ssh-agent:error while loading shared liberary 
libgssapi_krb5.so.2 : cannout open shared object file:no such file or directory


and it asks me to login into fale safe gnome for trouble shoot.
i am using ubuntu 6.06 lts for lurning linux shell scripts

---

### Post by mali2297 on 2008-08-19
In the menus at the login screen, you should be able to find an option to use fail safe gnome. If you manage to login that way, then open a terminal and enter
```

sudo apt-get install --reinstall libkrb53

```

If you can't log in using fail safe gnome, then reboot and choose recovery mode at startup. You should reach a console where you can enter the command above.

---

