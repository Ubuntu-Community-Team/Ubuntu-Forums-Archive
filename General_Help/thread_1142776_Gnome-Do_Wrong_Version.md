---
title: "Gnome-Do Wrong Version"
date: 2009-04-29
forum: General Help
---

### Post by lvleph on 2009-04-29
For some reason after adding the ppa for gnome-do on two computers one of the computers does not find the most up-to-date gnome-do. But here is the weird part. It does find the most up-to-date gnome-do plugins, but of course I can't install them. 

Computer That Does Not Find the Update
```
gnome-do:
  Installed: (none)
  Candidate: 0.6.1.0-0ubuntu2
  Version table:
     0.6.1.0-0ubuntu2 0
        500 http://us.archive.ubuntu.com intrepid/universe Packages
        100 /var/lib/dpkg/status

```

```
gnome-do-plugins:
  Installed: (none)
  Candidate: 0.8.1.1-0~intrepid~ppa2
  Version table:
     0.8.1.1-0~intrepid~ppa2 0
        500 http://ppa.launchpad.net intrepid/main Packages
     0.6.0.1+dfsg-0ubuntu2 0
        500 http://us.archive.ubuntu.com intrepid/universe Packages


```

Computer That Does Find Update
```

gnome-do:
  Installed: 0.8.0-0~intrepid~ppa1
  Candidate: 0.8.0-0~intrepid~ppa1
  Version table:
 *** 0.8.0-0~intrepid~ppa1 0
        100 /var/lib/dpkg/status
     0.6.1.0-0ubuntu2 0
        500 http://us.archive.ubuntu.com intrepid/universe Packages
     0.5.99.0-0~ppa1 0
        500 http://ppa.launchpad.net intrepid/main Packages

```

```
gnome-do-plugins:
  Installed: 0.8.1.1-0~intrepid~ppa2
  Candidate: 0.8.1.1-0~intrepid~ppa2
  Version table:
 *** 0.8.1.1-0~intrepid~ppa2 0
        500 http://ppa.launchpad.net intrepid/main Packages
        100 /var/lib/dpkg/status
     0.6.0.1+dfsg-0ubuntu2 0
        500 http://us.archive.ubuntu.com intrepid/universe Packages

```

---

### Post by hyperdude111 on 2009-04-29
The site "getdeb" has .debs for gnome do.

---

### Post by lvleph on 2009-04-29
Thank you. I knew there had to be a deb out there somewhere.

---

