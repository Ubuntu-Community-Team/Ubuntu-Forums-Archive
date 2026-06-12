---
title: "kdesu kfmclient, X Error: BadDevice"
date: 2007-04-02
forum: Desktop Environments
---

### Post by lptr on 2007-04-02
It is very nerving that I cannot start reliable kdesu kfmclient. This is what I will presented:
```
$ kdesu kfmclient openProfile filemanagement
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

DCOP seems to have massive problems. I found the following in /root. I renamed this machine three times. It seems that DCOPserver generated every time new instances.
```
$ ls -al /root/
insgesamt 492
drwxr-xr-x 12 root root   4096 2007-04-02 09:20 .
drwxr-xr-x 21 root root   4096 2007-03-26 08:40 ..
drwx------  2 root root   4096 2007-03-28 15:43 .aptitude
-rw-------  1 root root   4553 2007-03-31 23:34 .bash_history
-rw-r--r--  1 root root   2227 2006-12-20 16:50 .bashrc
-rw-r--r--  1 root root     55 2007-03-26 09:52 .DCOPserver_feisitix__0
lrwxrwxrwx  1 root root     29 2007-03-24 09:43 .DCOPserver_feisitix_:0 -> /root/.DCOPserver_feisitix__0
-rw-r--r--  1 root root     54 2007-04-02 09:20 .DCOPserver_feistix__0
lrwxrwxrwx  1 root root     28 2007-04-02 09:20 .DCOPserver_feistix_:0 -> /root/.DCOPserver_feistix__0
-rw-r--r--  1 root root     54 2007-03-24 09:27 .DCOPserver_fesitix__0
lrwxrwxrwx  1 root root     28 2007-03-24 09:27 .DCOPserver_fesitix_:0 -> /root/.DCOPserver_fesitix__0
-rw-r--r--  1 root root     53 2007-03-22 11:14 .DCOPserver_hordix__0
lrwxrwxrwx  1 root root     27 2007-03-22 11:14 .DCOPserver_hordix_:0 -> /root/.DCOPserver_hordix__0
```

1st: Is there a known workaround, so that I can start kfmclient as su PREDICTABLE? (Simply killing DCOP links in /root?)

2nd: If kfmclient does start (usually after fresh reboot it works one time :( ) for example when right clicking on /etc/samba/smb.conf presents me a context menu where kate can be selected. If doing this running kfmclient running as su then there comes a msg KDEinit failed running kate. In other words: It is not possible to start kate (or any other KDE/X application) in user context su started by kfmclient. Is there a known workaround (except starting kdesu kate separately and drag&drop files to open kate later)?

3rd: If upper fails how about GNOME desktop. Are there similar glitches in nautilus (was the name right)?

Thanks for some insights and hopefully solutions.

rob*

---

