---
title: "making sshd start on boot"
date: 2009-01-06
forum: General Help
---

### Post by Alex Flint on 2009-01-06
Hi there,

I'm running ubuntu 8.10 and I've installed openssh-server with aptitude. I can start sshd with "sudo /etc/init.d/ssh start" and it works fine, but I want it to start when I boot my computer. The links in /etc/rc{1,2,3,4,5}.d have been installed by the openssh-server package as expected:

$ ls -l /etc/rc*.d/*ssh*
lrwxrwxrwx 1 root root 13 2008-11-21 16:33 /etc/rc1.d/K84ssh -> ../init.d/ssh
lrwxrwxrwx 1 root root 13 2008-11-21 16:33 /etc/rc2.d/S16ssh -> ../init.d/ssh
lrwxrwxrwx 1 root root 13 2008-11-21 16:33 /etc/rc3.d/S16ssh -> ../init.d/ssh
lrwxrwxrwx 1 root root 13 2008-11-21 16:33 /etc/rc4.d/S16ssh -> ../init.d/ssh
lrwxrwxrwx 1 root root 13 2008-11-21 16:33 /etc/rc5.d/S16ssh -> ../init.d/ssh

I see no error messages on boot, but after boot sshd is not running ("ps aux | grep sshd" shows nothing and I cannot "ssh localhost"). What could be the problem here?

---

### Post by thedarkwinter on 2009-01-06
Hi Alex

Have a look at /var/log/auth.log, there may some some clues in there:

mine says

```

Jan  6 10:39:36 michael-laptop sshd[5346]: Server listening on :: port 22.
Jan  6 10:39:36 michael-laptop sshd[5346]: Server listening on 0.0.0.0 port 22.

```

cheers,
Michael

---

