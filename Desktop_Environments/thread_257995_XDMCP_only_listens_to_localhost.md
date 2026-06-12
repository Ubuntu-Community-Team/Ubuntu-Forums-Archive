---
title: "XDMCP only listens to localhost"
date: 2006-09-15
forum: Desktop Environments
---

### Post by jcpunk on 2006-09-15
I am running dapper and am fully up to date, here is the relavant part of my gdm.conf-custom

```

[xdmcp]
# Distributions: Ship with this off.  It is never a safe thing to leave out on
# the net.  Setting up /etc/hosts.allow and /etc/hosts.deny to only allow local
# access is another alternative but not the safest.  Firewalling port 177 is
# the safest if you wish to have xdmcp on.  Read the manual for more notes on
# the security of XDMCP.
Enable=true
# Honor indirect queries, we run a chooser for these, and then redirect the
# user to the chosen host.  Otherwise we just log the user in locally.
HonorIndirect=true
# Maximum pending requests.
#MaxPending=4
#MaxPendingIndirect=4
# Maximum open XDMCP sessions at any point in time.
#MaxSessions=16
# Maximum wait times.
#MaxWait=15
#MaxWaitIndirect=15
# How many times can a person log in from a single host.  Usually better to
# keep low to fend off DoS attacks by running many logins from a single host.
# This is now set at 2 since if the server crashes then GDM doesn't know for
# some time and wouldn't allow another session.
#DisplaysPerHost=2
# The number of seconds after which a non-responsive session is logged off.
# Better keep this low.
#PingIntervalSeconds=15
# The port.  177 is the standard port so better keep it that way.
#Port=177
# Willing script, none is shipped and by default we'll send hostname system id.
# But if you supply something here, the output of this script will be sent as
# status of this host so that the chooser can display it.  You could for
# example send load, or mail details for some user, or some such.
#Willing=/etc/gdm/Xwilling

[gui]

```

this command works perfectly ```
Xnest :1 -query localhost -once
``` but ```
Xnest :1 -query `ifconfig eth0 |grep 'inet addr' |awk '{print $2}'|cut -d':' -f2` -once
``` does not, I just get the black, gray and white checker board with the X mouse cursor.  Both commands report the below
```

_XSERVTransSocketOpenCOTSServer: Unable to open socket for inet6
_XSERVTransOpen: transport open failed for inet6/elschiw40471:1
_XSERVTransMakeAllCOTSServerListeners: failed to open listener for inet6
XDMCP warning: INET6 UDP socket creation failed
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/share/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/share/X11/fonts/OTF, removing from list!
Could not init font path element /usr/share/X11/fonts/CID/, removing from list!

```
but the one querying my IP address also says
```

XDM: too many retransmissions

```

I cannot for the life of me figure out why it listens on one interface and not the other..... I do not have iptables configured, so I know it isn't blocking me but I cannot think of what is. :confused: 
```

sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

Please help.

---

### Post by jcpunk on 2006-09-15
bump ](*,)

---

### Post by cwaldbieser on 2006-09-15
> **jcpunk said:**
> bump ](*,)

Try using the "-ac" flag to bypass the security checks.

---

### Post by jcpunk on 2006-09-18
Can do, only where would I put this switch, the /etc/init.d/gdm script doesn't seem to have it and the manpages for Xnest are also missing these options....

---

