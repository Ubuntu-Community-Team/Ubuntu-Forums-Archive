---
title: "Windows Synchronize"
date: 2005-05-24
forum: Desktop Environments
---

### Post by compaqdrew on 2005-05-24
On XP, there's a nifty little feature that lets me right-click on a network drive (SMB share) and hit "make available offline".  Now I can take the machine offline, edit the file, reconnect to the network, and it updates my changes on the network.

Any similar functionality for ubuntu?  Can I sync files over an SMB share possibly via a comamnd-line tool and/or GNOME?

Thanks

---

### Post by buldir on 2005-05-26
Are you familiar with rsync?

```
man rsync
```

The line I use is:

```
rsync -aHv --delete --progress /source/dir /destination/dir/
```

I am not sure if this works over the network via Samba.

---

### Post by mosestruong on 2006-08-01
Correct me if I'm wrong, but doesn't rsync requires the other machine to also have rsync running?

I currently have a network storage device which I would like to be able to access when my laptop is not connected to that network. Are there something similar (not java) that I could use?

---

### Post by buldir on 2006-08-02
> **mosestruong said:**
> Correct me if I'm wrong, but doesn't rsync requires the other machine to also have rsync running?
Yes. Checkout the following links:

[http://pigtail.net/LRP/printsrv/cygwin-sshd.html](http://pigtail.net/LRP/printsrv/cygwin-sshd.html)
[http://servers.linux.com/servers/04/11/04/0346256.shtml?tid=119&tid=47](http://servers.linux.com/servers/04/11/04/0346256.shtml?tid=119&tid=47)
[http://optics.ph.unimelb.edu.au/help/rsync/rsync_pc1.html](http://optics.ph.unimelb.edu.au/help/rsync/rsync_pc1.html)

I'm not sure about your second question.

---

