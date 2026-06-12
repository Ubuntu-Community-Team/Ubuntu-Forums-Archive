---
title: "Rsyslog Configuration Causes Ubuntu 10.04 to Hang During Boot"
date: 2011-11-01
forum: Desktop Environments
---

### Post by kfjethro on 2011-11-01
I'm trying to configure my Ubuntu 10.04 (32-bit PAE) machine so system log messages that match a pattern are written to a named fifo by the rsyslog daemon. Another program reading from the named fifo processes and displays the messages.

I added a new file: /etc/rsyslog.d/99-passthru.conf which contains a line of the form:  

*.crit |/var/spool/passthru

I created the named fifo "/var/spool/passthru" using mkfifo and make it world writeable.

If I reboot the system, it will hang during the boot process. The last message that gets printed is that the USB keyboard has been detected, I can get the boot to complete using alt-sysreq-E but it leaves my machine in an unknown state.

If I remove /var/spool/passthru, or just make it a regular file, then the system will reboot with no problems.

I don't suspect an error with my rsyslog configuration because I can create the named fifo after boot, and restart the rsyslog daemon with no problems.

Has anybody seen a similar problem ?

---

