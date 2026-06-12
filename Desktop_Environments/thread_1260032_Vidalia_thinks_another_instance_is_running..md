---
title: "Vidalia thinks another instance is running."
date: 2009-09-07
forum: Desktop Environments
---

### Post by ToshibaLaptoplinux on 2009-09-07
Every time I launch Vidalia I get the following message:

"Another Vidalia process is possibly already running. If there really is not another Vidalia process running, you can choose to continue anyway. Would you like to continue starting Vidalia?"

As best I can determine there is never another Vidalia process running and I just select continue with no problem. However it is annoying. Any ideas? Maybe I haven't configured something correctly?

Thanks

Ubuntu 9.04 Jaunty
Kernel Linux 2.6.28-11-generic
GNOME 2.26.1

on a Toshiba Dynabook; TX/760LS

---

### Post by rifter on 2010-04-04
> **ToshibaLaptoplinux said:**
> Every time I launch Vidalia I get the following message:

"Another Vidalia process is possibly already running. If there really is not another Vidalia process running, you can choose to continue anyway. Would you like to continue starting Vidalia?"

As best I can determine there is never another Vidalia process running and I just select continue with no problem. However it is annoying. Any ideas? Maybe I haven't configured something correctly?

Thanks

Ubuntu 9.04 Jaunty
Kernel Linux 2.6.28-11-generic
GNOME 2.26.1

on a Toshiba Dynabook; TX/760LS

Usually when you get this message vidalia is running.  If you do 

```

 ps -ef | grep vidalia

```

You should get results like

```

rifter   18143     1 94 09:39 ?        00:19:14 vidalia
rifter   18146 18143  0 09:39 ?        00:00:03 /usr/sbin/tor -f /home/rifter/.vidalia/torrc DataDirectory /home/rifter/.tor ControlPort 9051 CookieAuthentication 0
rifter   20068 27034  0 09:59 pts/4    00:00:00 grep vidalia

```

Even if you kill the vidalia process the tor process it started will still be there.  I think both processes have to quit in order for you not to get that message, and you do want them both to be gone before you restart vidalia.

---

### Post by forsubhi on 2011-10-03
please tell me how to kill this process 
rifter   20068 27034  0 09:59 pts/4    00:00:00 grep vidalia

---

### Post by ottosykora on 2011-10-04
in fact I realized that there is some bug in the whole story of current version of tor/vidalia

Vidalia seems to not check if the tor is really running or not, it seems to get it from some log file or so.

This happens to me too when tor was somehow closed suddenly (e.g. the computer crashed or so).
Even removing tor completely then , but leaving vidalia in place, will produce this message and then no tor is runninng for sure.

I found quick and dirty workaround: reinstall vidalia and the problem is cured.

---

