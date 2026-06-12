---
title: "pHpmyAdmin on shared hosted server?"
date: 2009-02-24
forum: General Help
---

### Post by Nixie Pixel on 2009-02-24
Hi, I was wondering if anyone had any advice on how I could, possibly through SSH tunneling, run phpmyAdmin on my local machine and administer my mySql databases on my (shared) hosted server?

Thanks!

---

### Post by Peter09 on 2009-02-24
phpmyadmin is a webinterface. You should be able to get to it by
```
ipaddressofyourhost/myphpmyadmin
```

also for anything which works from the command line you can use ssh.

install openssh-server on the host.
```

Then the command ssh -X <user>@<host> xterm
```

will open a terminal on the host. Many other commands can replace the xterm command

---

### Post by Nixie Pixel on 2009-02-24
Thanks, I think I was confused about what I'm talking about.

I was looking for a locally-run mySQL client that I could use rather than going through the hosted site's web interface.

(No wonder I couldn't get phpmyadmin to work on my computer, and why it needed apache, and why I couldn't stop the service...I'm an idiot...)

---

