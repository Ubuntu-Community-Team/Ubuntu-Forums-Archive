---
title: "minor startup irritant"
date: 2006-06-03
forum: Desktop Environments
---

### Post by pillu on 2006-06-03
hi all

during startup ununtu tries to synchronize the clock with ntp.ubunutulinux.org. However it shows an error message saying that name resolution fails temporarily. My network works absolutely fine. Is there any way to correct this and if not how do I tell it not to synchronize with the server.

Thanks
Anand

---

### Post by tonyr on 2006-06-03
Edit the file **/etc/ntp.conf**. You'll need to use **sudo** or **gksu**.  
Comment out the line that says **server ntp.ubuntu.com**.  In your case
it may actually be **server ntp.ubuntulinux.org**.  Uncomment the line that says
**#server pool.ntp.org**.  (**#** is the comment start character).  That
gets you a different **ntp** server. The server **ntp.ubuntulinux.org** may be stressed
as more users move to Dapper.

---

### Post by pillu on 2006-06-04
[QUOTE=tonyr]Edit the file **/etc/ntp.conf**. You'll need to use **sudo** or **gksu**.  
Comment out the line that says **server ntp.ubuntu.com**.  In your case
it may actually be **server ntp.ubuntulinux.org**.  Uncomment the line that says
**#server pool.ntp.org**.  (**#** is the comment start character).  That
gets you a different **ntp** server. The server **ntp.ubuntulinux.org** may be stressed
as more users move to Dapper.[/QUOTE]

OOPS...there is nothing in my /etc/ntp.conf...The file is there but its empty. Now I know what the problem is. Could you post the content of ur /etc/ntp.conf so that i can paste it in there ?

thanks

---

### Post by tonyr on 2006-06-04
You might check that you have package **ntp-simple** installed before
you do this.

Here ya go:
> 
# /etc/ntp.conf, configuration for ntpd

# ntpd will use syslog() if logfile is not defined
#logfile /var/log/ntpd

driftfile /var/lib/ntp/ntp.drift
statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).
#server ntp.your-provider.example

#server ntp.ubuntu.com

# pool.ntp.org maps to more than 100 low-stratum NTP servers.
# Your server will pick a different set every time it starts up.
#  *** Please consider joining the pool! ***
#  ***  <http://www.pool.ntp.org/#join>  ***
server pool.ntp.org

# ... and use the local system clock as a reference if all else fails
# NOTE: in a local network, set the local stratum of *one* stable server
# to 10; otherwise your clocks will drift apart if you lose connectivity.
server 127.127.1.0
fudge 127.127.1.0 stratum 13

# By default, exchange time with everybody, but don't allow configuration.
# See /usr/share/doc/ntp-doc/html/accopt.html for details.
restrict default kod notrap nomodify nopeer noquery

# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1 nomodify

# Clients from this (example!) subnet have unlimited access,
# but only if cryptographically authenticated
#restrict 192.168.123.0  mask  255.255.255.0 notrust

# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
#broadcast 192.168.123.255

# If you want to listen to time broadcasts on your local subnet,
# de-comment the next lines. Please do this only if you trust everybody
# on the network!
#disable auth
#broadcastclient




---

