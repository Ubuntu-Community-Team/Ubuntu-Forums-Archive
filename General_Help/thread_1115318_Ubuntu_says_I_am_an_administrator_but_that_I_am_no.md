---
title: "Ubuntu says I am an administrator but that I am not in the sudoers file?"
date: 2009-04-03
forum: General Help
---

### Post by GodAmoungMen on 2009-04-03
I cannot do things like run sudo commands or even do the update manager
This is the error I get when Trying to run update manger.

"The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator."


Here is my output from "id"
 
```
andy@crested:~$ id
uid=1000(andy) gid=1000(andy) groups=4(adm),20(dialout),24(cdrom),46(plugdev),10
8(lpadmin),123(admin),124(sambashare),1000(andy)

```

and here is is my output from 
 "sudo cat /etc/sudoers" (I didn't think I named my machine crested)
```

and@crested:~$ sudo cat/etc/sudoers
sudo: unable to resolve host crested
[sudo] password for andy:
andy is not in the sudoers file. This incident will be reported.
```

Hopefully someone can help!

---

### Post by taurus on 2009-04-03
Did you somehow modify your /etc/sudoers?

[http://www.psychocats.net/ubuntu/fixsudo#recoverymode](http://www.psychocats.net/ubuntu/fixsudo#recoverymode)

p.s.  There should be a space between cat and /etc/sudoers.

```
sudo cat /etc/sudoers
```

---

### Post by CyberMando on 2009-04-03
Try cat /etc/hostname. If it is what you thought you set the hostname to reboot and you will have sudo.

---

