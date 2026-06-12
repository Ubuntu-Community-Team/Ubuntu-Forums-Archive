---
title: "[SOLVED] root permission?"
date: 2008-12-11
forum: General Help
---

### Post by Zarakava on 2008-12-11
How do I give this to myself. I am trying to install something following instructions on this site.
[http://www.ubuntu-unleashed.com/2007/08/howto-setup-belkin-wireless-g-f5d7050.html](http://www.ubuntu-unleashed.com/2007/08/howto-setup-belkin-wireless-g-f5d7050.html)

however, when I get to command "make install", it says I don't have permission. I guess its trying to do something in root, so I need to be able to do this.

Ubuntu 8.10

---

### Post by Separ on 2008-12-11
Type ```
sudo make install
```

The password is the same as your user password.

---

### Post by geirha on 2008-12-11
To run a command as root, prepend it with sudo
```
sudo make install
```

Read more on [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by 7raTEYdCql on 2008-12-11
Just to explain to you.
 
There are certain commands on the computer which the generic user doesn't have access to. Therefore for the user to be able to use these commands he/she must become the administrator to perform them. TO become the administrator/super-user of the computer the command used is "sudo".

THerefore any administrative command to be performed by the generic user should be preceded by a sudo.

---

### Post by Zarakava on 2008-12-11
thanks. That solved that problem, but my USB dongle still hates me. :( thanks.

---

