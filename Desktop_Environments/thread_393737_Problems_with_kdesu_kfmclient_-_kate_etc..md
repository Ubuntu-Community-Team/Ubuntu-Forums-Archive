---
title: "Problems with kdesu kfmclient - kate etc."
date: 2007-03-26
forum: Desktop Environments
---

### Post by lptr on 2007-03-26
First of all: Quite often there are problems starting konqueror as kdesu. This is not only true for Feisty but also for Edgy, Dapper. Problems seemed to start with Breezy as far I can say; only in Hoary (5.04 still actively used, here - yes) it is predictable starting kdesu konqueror. If starting from console some strange DCOP messages appear. Sometimes messages like this are presented:

```
rob@feisitix:~$ kdesu kfmclient openProfile filemanagement
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
kfmclient: ERROR: Couldn't start konqueror from konqueror.desktop: KDEInit kann "konqueror" nicht starten.
```

If I need to have a second sudo'ed konqeror window the only way to get one is to Ctrl-N of the first as kdesu started instance (document / new window) - f.i. to copy move files or such.

Secondly I do wonder, why (if konqueror finally did start as su) it is not possible anymore to right click on ordinary cfg textfiles like /etc/hosts to edit them under context of root via kate or kwrite (open with). If doing this then the message 'KDEinit cannot start "kate"' appears. If Kate has been opened before as KDEsu (but not before konqueror otherwise konqueror will not start - well sometimes) then the file will be loaded into it. This all worked absolutely seamless in Hoary.

If I want to edit configuration files, I am forced very often to start sudo nano, mc or vi to edit files. This is quite boring. Because I did not switch away from Hoary as primary working platform, yet, - well, it was nerving but I could live with it. But now I'm willing to jump into a newer boat - now its getting painfull.

Anyone having an idea what I am doing wrong?

Forgot to mention: In /var/log/messages nothing appears that tells from the causal context of problems.

Any ideas?

rob*

---

### Post by lptr on 2007-10-27
Slowly I think I am the only one recognizing this problem?

I installed Gutsy - same with it. Sometimes I can start konqueror using kdesu, sometimes not. 

Boring

There is a new app: Dolphin. Seems to be replacement for the old filemanager in konqueror. It has a button that allows running instance as root. Maybe this solves the troubles not being able to easily manipulate files in graphical ways. 

rob*

---

### Post by usp8riot on 2007-10-27
It seems to be a bug in Kdesu involving permissions. I updated to the one discussed in the link and problem was solved. [https://bugs.launchpad.net/ubuntu/gutsy/+source/kdesudo/+bug/155032](https://bugs.launchpad.net/ubuntu/gutsy/+source/kdesudo/+bug/155032)

Unofficial patched version: [http://ubuntu.lnix.net/misc/kdesudo_1.1-0ubuntu5_i386.deb](http://ubuntu.lnix.net/misc/kdesudo_1.1-0ubuntu5_i386.deb)

---

### Post by lptr on 2007-10-28
Thanks for answer. I read into this, too. 

With current (default) packages from Canonical for example the command 

$ kdesudo kate 

results in 
Error: "/var/tmp/kdecache-roberts" is owned by uid 1000 instead of 0.
same error for /tmp/ksocket-roberts and /tmp/kde-roberts

This kate session comes up and runs in root context. 

When doing

$ kdesudo kfmclient openProfile filemanagement

Konqueror opens but is not running as root.

Ok I know this would better fit into bugzilla instead of here. 

This morning I started playing around with Dolphin. This one seems to solve my main issue: Having a root environment for deleting files, editing files that are owned by root. Since 5.40 (Hoary) I was digging around on command line with nano / mc / vi . I felt as being thrown back into last millenium.

Dolphin seems to bring the long awaited work around. Now I have to solve that dammned UTF-8 thing with SAMBA and the file content. Then I could move over new version. 

rob*

---

