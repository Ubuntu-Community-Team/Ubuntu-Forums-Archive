---
title: "OpenSSH installation failed."
date: 2009-06-10
forum: General Help
---

### Post by valex on 2009-06-10
I tried to install openSSH using terminal then I got following error message.
I used this command.
```
sudo apt-get install openssh-client
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssh-client is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 39 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up hwtest-desktop (0.1-0ubuntu1) ...
/var/lib/dpkg/info/hwtest-desktop.config: 4: /usr/share/hwtest/install/config: not found
dpkg: error processing hwtest-desktop (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 hwtest-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

how is this happened and how do I install openSSH?

---

### Post by DGortze380 on 2009-06-10
what are you trying to do?

Client should be installed by default, just type at the commandline 
```

ssh user@host

```

If you want to connect TO this machine, you want 
```

sudo apt-get install openssh-server

```

---

