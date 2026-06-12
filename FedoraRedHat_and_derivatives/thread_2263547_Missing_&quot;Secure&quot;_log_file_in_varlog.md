---
title: "Missing &quot;Secure&quot; log file in /var/log"
date: 2015-02-01
forum: Fedora/RedHat and derivatives
---

### Post by Aphexlog on 2015-02-01
I am missing the "Secure" log file, of which I should be able to use to fined failed log in attempts, etc.
Here is what the /var/log file contains (from my fedora 20 distro):

[awest@Loki log]$ ls
anaconda  btmp           cups        dnf.rpm.log  journal  ppp     speech-dispatcher  wtmp            yum.log
audit     btmp-20150201  custom.log  gdm          lastlog  README  sssd               Xorg.0.log
boot.log  chrony         dnf.log     glusterfs    pluto    samba   tallylog           Xorg.0.log.old

Any help would be greatly appreciated :)

---

### Post by nerdtron on 2015-02-01
anaconda? yum? This is a Red hat/Centos system right? And this is Ubuntu Forums. :)

Anyway, I believe the secure.log is called the audit.log? (not sure)

---

### Post by Irihapeti on 2015-02-01
*Thread moved to **Fedora/RedHat and derivatives**.*

---

### Post by Aphexlog on 2015-02-01
Never mind actually :)
Just in case if anyone stumbles by this and has the same issue...
Most newer versions Linux distros use the journalctl command to view system logs
use man to get further details regarding journalctl and modifiers
use "journalctl|grep [string] to search specific text

---

