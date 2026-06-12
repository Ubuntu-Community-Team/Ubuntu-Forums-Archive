---
title: "Ubuntu 7.10 and Dell OMSA - Finally got it working"
date: 2008-04-04
forum: Dell  Ubuntu Support
---

### Post by wtijr on 2008-04-04
I finally got Dell OMSA working on my PowerEdge servers with Ubuntu 7.10. The information I needed to accomplish this was scattered over the forums so I wanted to give back by putting it all together in one post. Here goes:

First download the latest deb OMSA distribution from:

[ftp://ftp.sara.nl/pub/sara-omsa/dists/dell/sara/binary-i386](ftp://ftp.sara.nl/pub/sara-omsa/dists/dell/sara/binary-i386)

Install the package with the GDebi Package installer.

(now this bit was hard to find)
ADD the following to the /etc/ld.so.conf file:

include /opt/dell/srvadmin/dataeng/bin
include /opt/dell/srvadmin/hapi/bin
include /opt/dell/srvadmin/oma/bin
include /opt/dell/srvadmin/omsa/bin
include /opt/dell/srvadmin/shared/bin
include /opt/dell/srvadmin/sm
include /opt/dell/srvadmin/sm/dellvl

Next, install SNMP:

sudo apt-get install snmp snmpd

start OMSA:

sudo /etc/init.d/dataeng enablesnmp

sudo /etc/init.d/dataeng start

start the OMSA web interface:

sudo /etc/init.d/dsm_om_connsvc start

You should now be able to access OMSA at:

https://<server name/ip address>:1311

Thank you to all of those that discovered and posted this information. Hopefully, having this information in one post will be helpful and time-saving to those to come.

---

### Post by jdwannam on 2008-04-23
I was able to get OMSA working on a PowerEdge 1950 with Ubuntu 7.10 using this mini-guide.

There are a few extra bits of information I'd like to add:

After running /etc/init.d/dataeng enablesnmp, the /etc/snmpd.conf file is modified to add:

```

# Allow Systems Management Data Engine SNMP to connect to snmpd using SMUX
smuxpeer .1.3.6.1.4.1.674.10892.1

```

Also, the ubuntu distributed snmpd.conf has this in the access line:
```
access  notConfigGroup ""      any       noauth    exact  systemview none none
```

which gets changed to 

```
access  notConfigGroup ""      any       noauth    exact  all none none
```

In order for this to work, a new view has to also be defined called "all".  After adding this line:

```
view     all    included   .1
```

I was able to retreive data with snmpwalk on a remote host.  However, I still could not receive the dell OMSA OIDs.

The fix I found is to modify /etc/default/snmpd and change the default options to remove -I smux

so I changed from:

```
SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid 10.10.10.10'
```

to

```
SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -p /var/run/snmpd.pid 10.10.10.10'
```

After changing that file and restarting snmpd, the Dell specific OIDs were being reported with snmpwalk on my network management server.  (Zenoss in this case)

Thanks for the original post!

---

### Post by meese7en on 2008-04-26
Thanks for the guide. I've managed to get omsa working on my R200 with Hardy on it.
But the problem is I cannot login. I used normal and root account, but still, login failed. How to solve this ?

---

### Post by jtopping on 2008-04-29
If you have 64bit debian/ubuntu, use this guide:
[http://blog.loftninjas.org/?p=100](http://blog.loftninjas.org/?p=100)

---

### Post by jtopping on 2008-04-29
or check out my blog page on it:
[http://blog.zztopping.com/2008/04/29/dell-omsa-debian-64bit/](http://blog.zztopping.com/2008/04/29/dell-omsa-debian-64bit/)

---

### Post by meese7en on 2008-04-29
Thanks, it works great !

---

### Post by quad3d@work on 2008-05-23
Works with PE2950 and PERC 6/i on 8.04 AMD64.

Instead downloading the Debian debs, I downloaded the Ubuntu ones.

---

### Post by oneloveamaru on 2008-06-05
> **wtijr said:**
> I finally got Dell OMSA working on my PowerEdge servers with Ubuntu 7.10. The information I needed to accomplish this was scattered over the forums so I wanted to give back by putting it all together in one post. Here goes:

First download the latest deb OMSA distribution from:

[ftp://ftp.sara.nl/pub/sara-omsa/dists/dell/sara/binary-i386](ftp://ftp.sara.nl/pub/sara-omsa/dists/dell/sara/binary-i386)

Install the package with the GDebi Package installer.

(now this bit was hard to find)
ADD the following to the /etc/ld.so.conf file:

include /opt/dell/srvadmin/dataeng/bin
include /opt/dell/srvadmin/hapi/bin
include /opt/dell/srvadmin/oma/bin
include /opt/dell/srvadmin/omsa/bin
include /opt/dell/srvadmin/shared/bin
include /opt/dell/srvadmin/sm
include /opt/dell/srvadmin/sm/dellvl

Next, install SNMP:

sudo apt-get install snmp snmpd

start OMSA:

sudo /etc/init.d/dataeng enablesnmp

sudo /etc/init.d/dataeng start

start the OMSA web interface:

sudo /etc/init.d/dsm_om_connsvc start

You should now be able to access OMSA at:

https://<server name/ip address>:1311

Thank you to all of those that discovered and posted this information. Hopefully, having this information in one post will be helpful and time-saving to those to come.

wtijr, you have no idea how happy I am right now. I have been trying to get Zabbix to work for a couple months now. Had my HP's right up and running.. but these Dells....  I tell ya, are a pain! I took the smux out of /etc/default/snmpd, added those lines into /etc/ld.so.conf and bang!!!!!!!!, started working!! Now my Zabbix works and I can actually do snmpwalks and get responses!!!


Where did you find those lines for /etc/ld.so,conf anyways? I found something that said remove the -I smux but that alone didn't work. Never found anything related to /etc/ld.so.conf. I was also searching using Debian and not Ubuntu, as the servers are running Debian Etch, which the great Ubuntu is built from. :) Of course Desktops are running Kubuntu. We like KDE here.

Seriously though, if you are ever in the Tampa Bay area, I owe you a few beers!

---

