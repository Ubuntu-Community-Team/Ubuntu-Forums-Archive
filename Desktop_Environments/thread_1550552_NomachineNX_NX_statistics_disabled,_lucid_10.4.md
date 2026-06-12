---
title: "NomachineNX: NX statistics disabled, lucid 10.4"
date: 2010-08-11
forum: Desktop Environments
---

### Post by Exeneva on 2010-08-11
I've followed the guide here up to step 9: [http://ubuntuforums.org/showthread.php?t=1546856](http://ubuntuforums.org/showthread.php?t=1546856)

However, on step 10, I have the following error:

> sudo /etc/init.d/nxserver restart
NX> 123 Service stopped.
NX> 153 Stopping NX server monitor.
NX> 153 NX server monitor already stopped.
NX> 122 Service started.
NX> 999 Bye.
NX> 723 Cannot start NX statistics:
NX> 709 NX statistics are disabled for this server.
NX> 999 Bye.


I have OpenSSH server installed, and my sshd config file has statistics enabled:

> #
# Enable or disable statistics:
#
# 1: Enabled. Enable the production of NX statistics.
#
# 0: Disabled. Disable the production of NX statistics.
# 
# Run the nxstat daemon in background. This daemon can be used to
# produce statistics about the NX services and the node host machine
# either for localhost and any of the available nodes when the load
# balancing is enabled. This requires that the nxsensor daemon is
# started on each of the node machines.
#
#EnableStatistics = "1"


Not sure what the problem is. Can someone help me out? Thanks.

---

### Post by Exeneva on 2010-08-16
No one?

---

### Post by logoff on 2012-06-15
so late, but: have you noticed that the line is commented? you must eliminate the '#' to enable any configuration. like this:


> #
# Enable or disable statistics:
#
# 1: Enabled. Enable the production of NX statistics.
#
# 0: Disabled. Disable the production of NX statistics.
# 
# Run the nxstat daemon in background. This daemon can be used to
# produce statistics about the NX services and the node host machine
# either for localhost and any of the available nodes when the load
# balancing is enabled. This requires that the nxsensor daemon is
# started on each of the node machines.
#
EnableStatistics = "1"

---

