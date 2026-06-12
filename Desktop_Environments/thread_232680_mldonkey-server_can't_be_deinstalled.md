---
title: "mldonkey-server can't be deinstalled"
date: 2006-08-09
forum: Desktop Environments
---

### Post by zardoz on 2006-08-09
Hy!

I just wanted to remove mldonkey + server from my system, but under synaptic I get the following messages, when trying to remove mldonkey-server:

E: mldonkey-server: subprocess pre-removal script returned error exit status 1

Terminal:
Removing mldonkey-server ...
Stopping MLDonkey: mlnetNo process in pidfile `/var/run/mlnet.pid' found running; none killed.
invoke-rc.d: initscript mldonkey-server, action "stop" failed.
dpkg: error processing mldonkey-server (--remove):
 subprocess pre-removal script returned error exit status 1
Starting MLDonkey: mlnet configuration file prevent mlnet to be started (use force-start).
Errors were encountered while processing:
 mldonkey-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


What should I do? Write to the package maintainer?

Best regards,
Kai

---

### Post by mlind on 2006-08-09
That's probably a packaging bug. pre-removal script fails because it can't find running instance of mldonkey-server which sounds quite stupid. 
Try to start mldonkey-server, then remove the package.

---

### Post by zardoz on 2006-08-09
Also tried this ... without success. Same error messages.

---

### Post by mlind on 2006-08-09
Is there a file called /var/lib/dpkg/info/mldonkey-server.prerm ?
(And could you post it here)

---

### Post by jeff777 on 2006-08-09
I am having exactly the same problem.  Here is /var/lib/dpkg/info/mldonkey-server.prerm:

cat /var/lib/dpkg/info/mldonkey-server.prerm
#!/bin/sh
set -e
# Automatically added by dh_installinit
if [ -x "/etc/init.d/mldonkey-server" ]; then
        if [ -x "`which invoke-rc.d 2>/dev/null`" ]; then
                invoke-rc.d mldonkey-server stop || exit $?
        else
                /etc/init.d/mldonkey-server stop || exit $?
        fi
fi
# End automatically added section

---

### Post by jeff777 on 2006-08-09
This thread solved the problem for me.

[http://ubuntuforums.org/showthread.php?t=201785](http://ubuntuforums.org/showthread.php?t=201785)

---

### Post by mlind on 2006-08-10
> **jeff777 said:**
> This thread solved the problem for me.

[http://ubuntuforums.org/showthread.php?t=201785](http://ubuntuforums.org/showthread.php?t=201785)

That should work. Commenting out lines in /var/lib/dpkg/info/mldonkey-server.prerm should solve it too.

---

### Post by zardoz on 2006-08-10
Commenting out what lines exactly?

```

#!/bin/sh
set -e
# Automatically added by dh_installinit
if [ -x "/etc/init.d/mldonkey-server" ]; then
        if [ -x "`which invoke-rc.d 2>/dev/null`" ]; then
                invoke-rc.d mldonkey-server stop || exit $?
        else
                /etc/init.d/mldonkey-server stop || exit $?
        fi
fi
# End automatically added section

```

---

### Post by zardoz on 2006-08-10
Ok, got it ... simply commented the whole if block out there ... thanks a lot.

---

