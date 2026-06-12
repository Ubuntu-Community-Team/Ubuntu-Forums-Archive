---
title: "samba reinstall problem"
date: 2006-06-04
forum: Desktop Environments
---

### Post by louis_nichols on 2006-06-04
I tried samba today and couldn't get it to work, so I uninstalled it. It gave me an error about rc-update not being able to run roght, because of some bad link (/etc/rc3.d/K09-samba I think), so I deleted the link by hand and thought things were ok.

Then I said to myself I should give it another try, but can't get it to install properly. I always get the error:

```
Setting up samba (3.0.22-1ubuntu3) ...
Generating /etc/default/samba...
* Starting Samba daemons...                                                                                                                          [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up samba (3.0.22-1ubuntu3) ...
* Starting Samba daemons...                                                                                                                          [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing: samba
```

I tried all kind of things: purging the package again, manually deleting files I that I found in /etc that are connected to samba... but nothing

Any ideas?

---

### Post by rbalfour on 2006-06-04
Have you tried

> apt-get -f install

---

### Post by louis_nichols on 2006-06-04
Thanks for the reply. I tried that too, but still no go :(

---

