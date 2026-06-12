---
title: "Home dir on NFS gives problems"
date: 2013-05-15
forum: Desktop Environments
---

### Post by GizahNL on 2013-05-15
Hey,

when I configure my fstab to mount my homedir using NFS I get lots of problems:
-logging in using the graphic enviroment doesn't work
-logging in on one of the virtual terminals (tty1 etc) does however I get the error message that my homedir is unavailable.

It seems that at boot time the NFS share is not correctly mounted!

```

10.168.0.3:/tank/data/home    /home    nfs        defaults,noatime,hard,intr,rsize=32768,wsize=32768    0    0

```

---

### Post by SeijiSensei on 2013-05-15
If you want to do this, you'll need to [set up networking manually]("https://help.ubuntu.com/12.04/serverguide/network-configuration.html#ip-addressing") by editing /etc/network/interfaces so the network will start at boot and mount the NFS share before getting to the login phase.

---

### Post by steeldriver on 2013-05-15
... or you could use autofs to mount it on demand

---

### Post by SeijiSensei on 2013-05-15
How would that work if his home directory is on the server?  He cannot use a GUI-based client like NetworkManager since he would need access to his GUI, but he cannot get his GUI until the network is up and the NFS share mounted.

Maybe there is some feature of autofs that I'm missing, but I don't see how you can access files on a network share until the network is running.

---

### Post by steeldriver on 2013-05-15
Oops yes you're right - I mount my /nfs/home separately via autofs just as a data dir (Documents Pictures etc), the actual ~/.config files and so on are on a small local /home

That still may be an option for the OP (or a version of it with bind mounts) - but I agree it's not exactly an autofs-mounted home

My apologies

---

### Post by GizahNL on 2013-05-18
> **SeijiSensei said:**
> If you want to do this, you'll need to [set up networking manually]("https://help.ubuntu.com/12.04/serverguide/network-configuration.html#ip-addressing") by editing /etc/network/interfaces so the network will start at boot and mount the NFS share before getting to the login phase.
Thanks! That indeed did fix the issue of mounting at boot time :)

However for some reason logging into the graphical environment (console is ok) even with a freshly created user takes _very very_ long (over 10 minutes) and after the wait the desktop is still unworkably slow.
Doing a bonnie++ shows read/write speeds of over 60MB/s 

Watching network activity using nfsiostat show no activity during the login procedure.

btw I seem to have placed my topic in the wrong sub-forum (I was thinking desktop environment as opposed to server ;) ) a mod care to move it ?

---

### Post by GizahNL on 2013-05-21
shameless bumping ;)

---

### Post by pmackinney on 2014-04-28
I know this is an old thread, but the title is so generic that it matches my problems exactly. My homedir is on an NFS volume, with automount and yp/nis all is good. BUT....

With this situation, the local root has less permissions on my homedir than my user account does, and a lot of services seem to want to write config files in my homedir as root. Shouldn't services write config files in your homedir as you?

My system is a new 14.04 install, the server is some other Linux distro.

A sample from /var/log/syslog:

Apr 28 12:07:53 ws6 pulseaudio[11560]: [pulseaudio] core-util.c: Home directory not accessible: Permission denied
Apr 28 12:08:28 ws6 kernel: [356819.943175] type=1400 audit(1398712108.565:1942): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/mission-control-5" name="/net/my_server/data/users/my_handle/.config/libaccounts-glib/accounts.db" pid=12547 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=615 ouid=615
Apr 28 12:08:28 ws6 kernel: [356819.946636] type=1400 audit(1398712108.569:1943): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/mission-control-5" name="/net/my_server/data/users/my_handle/.config/dconf/user" pid=12547 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=615 ouid=615
Apr 28 12:08:28 ws6 kernel: [356820.052156] type=1400 audit(1398712108.673:1944): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/mission-control-5" name="/net/my_server/data/users/my_handle/.mission-control/accounts/accounts.cfg" pid=12547 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=615 ouid=615
Apr 28 12:08:28 ws6 kernel: [356820.052290] type=1400 audit(1398712108.673:1945): apparmor="DENIED" operation="mkdir" profile="/usr/lib/telepathy/mission-control-5" name="/net/my_server/data/users/my_handle/.local/share/telepathy/" pid=12547 comm="mission-control" requested_mask="c" denied_mask="c" fsuid=615 ouid=615
Apr 28 12:08:28 ws6 kernel: [356820.057138] type=1400 audit(1398712108.677:1947): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/mission-control-5" name="/net/my_server/data/users/my_handle/.cache/.mc_connections" pid=12547 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=615 ouid=615

---

