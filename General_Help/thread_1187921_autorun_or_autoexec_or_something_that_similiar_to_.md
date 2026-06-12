---
title: "autorun or autoexec or something that similiar to it?"
date: 2009-06-15
forum: General Help
---

### Post by soulhealer on 2009-06-15
where do i set things that i want to start whenever ubuntu rebooted without having to login desktop first? because my:
1. remote desktop
2. mysql
3. clamav-daemon
4. samba file sharing
is not automatically started whenever the system get rebooted.
except for remote destkop, it is started after i login the desktop manually and locally. the others, needed to be started on terminal. I enter these everytime i rebooted:
```

sudo service samba stop;sudo fusermount -u /sambashare;sudo service clamav-daemon restart;sudo clamfs /etc/clamfs/clamfs.xml;sudo service samba start

```i'm not always around the computer, so if i'm not there, others won't be able to use that system.

thanks for any kind of help or advice.

regards,
William.

---

### Post by sedawk on 2009-06-15
Basically all software packages with some daemons also bring some
startup script. This startup script normally is located in
/etc/init.d

E.g. I have 
/etc/init.d/clamav-freshclam

To really activate such a script there are symbolic links
from /etc/init.d/rc2.d startup scripts (S<num>*) to the
scripts in /etc/init.d.
(The prefix S<num> is a startup script and the numbers control
 the sequence. The prefix K<num> is for running the startup scripts
 with a "stop" parameter).

If your software comes without startup scripts you can try to 
use an existing one as a template.

Tools which need to be started once but do not run as
daemons can be added to /etc/rc.local

---

### Post by scrooge_74 on 2009-06-15
When you install samba it will also install it deamons, you only need to configure samba to fit your needs.

Same goes for the rest, you could see them running if you check your start up logs or check which process are running or are dormant.

---

### Post by soulhealer on 2009-06-17
i see, but the script is still confusing me...
how do i make script for:
```
sudo clamfs /etc/clamfs/clamfs.xml
```
at the moment, it must be re-mounted anytime i rebooted.

---

### Post by soulhealer on 2009-06-17
it seems too that mysql service failed to start since ip hasn't been set when it is starting... perhaps i should change the sequence? if so, please set an example here if you don't mind.

anyway, here's my log:
```

Jun 17 22:40:21 myserv mysqld[3132]: 090617 22:40:21  InnoDB: Started; log sequence number 0 43655
Jun 17 22:40:21 myserv mysqld[3132]: 090617 22:40:21 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
Jun 17 22:40:21 myserv mysqld[3132]: 090617 22:40:21 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Jun 17 22:40:21 myserv mysqld[3132]: 090617 22:40:21 [ERROR] Aborting
Jun 17 22:40:21 myserv mysqld[3132]: 
Jun 17 22:40:21 myserv mysqld[3132]: 090617 22:40:21  InnoDB: Starting shutdown...
Jun 17 22:40:21 myserv console-kit-daemon[2494]: WARNING: Couldn't read /proc/2493/environ: Failed to open file '/proc/2493/environ': No such file or directory 
Jun 17 22:40:22 myserv mysqld[3132]: 090617 22:40:22  InnoDB: Shutdown completed; log sequence number 0 43655
Jun 17 22:40:22 myserv mysqld[3132]: 090617 22:40:22 [Note] /usr/sbin/mysqld: Shutdown complete
Jun 17 22:40:22 myserv mysqld[3132]: 
Jun 17 22:40:22 myserv mysqld_safe[3276]: ended
Jun 17 22:40:23 myserv NetworkManager: <info>  (eth3): device state change: 1 -> 2 
Jun 17 22:40:23 myserv NetworkManager: <info>  (eth3): bringing up device. 
Jun 17 22:40:23 myserv NetworkManager: <info>  (eth3): preparing device. 
Jun 17 22:40:23 myserv NetworkManager: <info>  (eth3): deactivating device (reason: 2). 
Jun 17 22:40:23 myserv NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Jun 17 22:40:23 myserv NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Jun 17 22:40:23 myserv NetworkManager: <info>  (eth2): device state change: 1 -> 2 
Jun 17 22:40:23 myserv NetworkManager: <info>  (eth2): bringing up device. 
Jun 17 22:40:23 myserv NetworkManager: <info>  (eth2): preparing device. 
Jun 17 22:40:23 myserv NetworkManager: <info>  (eth2): deactivating device (reason: 2). 
Jun 17 22:40:23 myserv NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Jun 17 22:40:23 myserv nm-system-settings: Added default wired connection 'Auto eth2' for /org/freedesktop/Hal/devices/net_00_02_44_6d_fc_64
Jun 17 22:40:23 myserv NetworkManager: <info>  (eth1): device state change: 1 -> 2 
Jun 17 22:40:23 myserv NetworkManager: <info>  (eth1): bringing up device. 
Jun 17 22:40:23 myserv NetworkManager: <info>  (eth1): preparing device. 
Jun 17 22:40:23 myserv NetworkManager: <info>  (eth1): deactivating device (reason: 2). 
Jun 17 22:40:23 myserv NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Jun 17 22:40:23 myserv NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Jun 17 22:40:23 myserv NetworkManager: <info>  (eth0): bringing up device. 
Jun 17 22:40:23 myserv NetworkManager: <info>  (eth0): preparing device. 
Jun 17 22:40:23 myserv NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Jun 17 22:40:23 myserv nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_02_44_73_e7_e3
Jun 17 22:40:23 myserv NetworkManager: <info>  (eth1): carrier now ON (device state 2) 
Jun 17 22:40:23 myserv NetworkManager: <info>  (eth1): device state change: 2 -> 3 
Jun 17 22:40:23 myserv nm-system-settings: Added default wired connection 'Auto eth3' for /org/freedesktop/Hal/devices/net_00_02_44_87_69_0d
Jun 17 22:40:23 myserv NetworkManager: <info>  Activation (eth1) starting connection 'Auto eth1' 
Jun 17 22:40:23 myserv NetworkManager: <info>  (eth1): device state change: 3 -> 4 
Jun 17 22:40:23 myserv NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jun 17 22:40:23 myserv NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jun 17 22:40:23 myserv NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jun 17 22:40:23 myserv NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jun 17 22:40:23 myserv NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jun 17 22:40:23 myserv NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Jun 17 22:40:23 myserv NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Jun 17 22:40:23 myserv NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Jun 17 22:40:23 myserv NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jun 17 22:40:23 myserv NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Jun 17 22:40:23 myserv NetworkManager: <info>  (eth1): device state change: 5 -> 7 
Jun 17 22:40:23 myserv NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Jun 17 22:40:23 myserv NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Jun 17 22:40:23 myserv NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Jun 17 22:40:23 myserv NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jun 17 22:40:23 myserv NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Jun 17 22:40:23 myserv NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Jun 17 22:40:23 myserv avahi-daemon[2976]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.176.
Jun 17 22:40:23 myserv avahi-daemon[2976]: New relevant interface eth1.IPv4 for mDNS.
Jun 17 22:40:23 myserv avahi-daemon[2976]: Registering new address record for 192.168.0.1 on eth1.IPv4.

```

---

### Post by Polaris96 on 2009-06-17
startup scripts are executed in the order they appear in the rc#.d directory (# is replaced by whatever runlevel.  ubuntu is usually 2).  You can try to reorder the execution of the process by copying it to a different process number.  Do not erase the original link, instead prepend a "_" which will tell init not to call it. (initi only cares about processes starting with "S" or "K" (start/kill))

example:  let's make process 2 become process 5

s10ioctl
s20kerneld
s30netbase
s60syslogd

1.  first we do this:  cp s20kerneld s50kerneld
2.  then we do this mv s20kerneld _s20kerneld (mv will rename files as well as moving them)
3.  then we a re left with

_s20kerneld
s10ictl
s30netbase
s50kerneld
s60syslogd

You can alter the precedence of any process in rc*.d this way

---

### Post by soulhealer on 2009-06-18
i, originally, had:
```
S17mysql-ndb-mgm
S18mysql-ndb
S19mysql
S50avahi-daemon
S50NetworkManager
etc...
```then i mv(renamed them, the mysql, into):
```
S50avahi-daemon
S50NetworkManager
S91mysql-ndb-mgm
S92mysql-ndb
S93mysql
etc...
```it still doesn't work, i checked the log, mysql still on the top of the NetworkManager service.
and then i did the same thing to RC1.d where the K(nums) are, as suggested before. still doesn't work.
here is my last log:
```
Jun 17 22:57:05 winetserv acpid: client connected from 2939[0:0] 
Jun 17 22:57:05 winetserv NetworkManager: <info>  starting... 
Jun 17 22:57:05 winetserv NetworkManager: <info>  (eth3): new Ethernet device (driver: '8139too') 
Jun 17 22:57:05 winetserv NetworkManager: <info>  (eth3): exported as /org/freedesktop/Hal/devices/net_00_02_44_87_69_0d 
Jun 17 22:57:05 winetserv NetworkManager: <info>  (eth2): new Ethernet device (driver: '8139too') 
Jun 17 22:57:05 winetserv NetworkManager: <info>  (eth2): exported as /org/freedesktop/Hal/devices/net_00_02_44_6d_fc_64 
Jun 17 22:57:05 winetserv NetworkManager: <info>  (eth1): new Ethernet device (driver: '8139too') 
Jun 17 22:57:05 winetserv NetworkManager: <info>  (eth1): exported as /org/freedesktop/Hal/devices/net_00_02_44_88_74_6b 
Jun 17 22:57:05 winetserv NetworkManager: <info>  (eth0): new Ethernet device (driver: '8139too') 
Jun 17 22:57:05 winetserv NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_02_44_73_e7_e3 
Jun 17 22:57:05 winetserv NetworkManager: <info>  (ttyS0): ignoring due to lack of mobile broadband capabilties 
Jun 17 22:57:05 winetserv NetworkManager: <info>  Trying to start the supplicant... 
Jun 17 22:57:05 winetserv NetworkManager: <info>  Trying to start the system settings daemon... 
Jun 17 22:57:05 winetserv nm-system-settings:    SCPlugin-Ifupdown: init!
Jun 17 22:57:05 winetserv nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Jun 17 22:57:05 winetserv nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Jun 17 22:57:05 winetserv nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_02_44_6d_fc_64, iface: eth2): not well known
Jun 17 22:57:05 winetserv nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_02_44_88_74_6b, iface: eth1): not well known
Jun 17 22:57:05 winetserv nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_02_44_73_e7_e3, iface: eth0): not well known
Jun 17 22:57:05 winetserv nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_02_44_87_69_0d, iface: eth3): not well known
Jun 17 22:57:05 winetserv nm-system-settings:    SCPlugin-Ifupdown: end _init.
Jun 17 22:57:05 winetserv nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun 17 22:57:05 winetserv nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun 17 22:57:05 winetserv nm-system-settings:    SCPlugin-Ifupdown: (162785192) ... get_connections.
Jun 17 22:57:05 winetserv nm-system-settings:    SCPlugin-Ifupdown: (162785192) ... get_connections (managed=false): return empty list.
Jun 17 22:57:05 winetserv nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Jun 17 22:57:05 winetserv avahi-daemon[2985]: Found user 'avahi' (UID 110) and group 'avahi' (GID 119).
Jun 17 22:57:05 winetserv avahi-daemon[2985]: Successfully dropped root privileges.
Jun 17 22:57:05 winetserv avahi-daemon[2985]: avahi-daemon 0.6.23 starting up.
Jun 17 22:57:05 winetserv avahi-daemon[2985]: Successfully called chroot().
Jun 17 22:57:05 winetserv avahi-daemon[2985]: Successfully dropped remaining capabilities.
Jun 17 22:57:05 winetserv avahi-daemon[2985]: No service file found in /etc/avahi/services.
Jun 17 22:57:05 winetserv avahi-daemon[2985]: Network interface enumeration completed.
Jun 17 22:57:05 winetserv avahi-daemon[2985]: Registering HINFO record with values 'I686'/'LINUX'.
Jun 17 22:57:05 winetserv avahi-daemon[2985]: Server startup complete. Host name is winetserv.local. Local service cookie is 3409586900.
Jun 17 22:57:08 winetserv mysqld_safe[3258]: started
Jun 17 22:57:09 winetserv console-kit-daemon[2503]: WARNING: Couldn't read /proc/2502/environ: Failed to open file '/proc/2502/environ': No such file or directory 
Jun 17 22:57:09 winetserv mysqld[3261]: 090617 22:57:09  InnoDB: Started; log sequence number 0 43655
Jun 17 22:57:09 winetserv mysqld[3261]: 090617 22:57:09 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
Jun 17 22:57:09 winetserv mysqld[3261]: 090617 22:57:09 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Jun 17 22:57:09 winetserv mysqld[3261]: 090617 22:57:09 [ERROR] Aborting
Jun 17 22:57:09 winetserv mysqld[3261]: 
Jun 17 22:57:09 winetserv mysqld[3261]: 090617 22:57:09  InnoDB: Starting shutdown...
Jun 17 22:57:10 winetserv NetworkManager: <info>  (eth3): device state change: 1 -> 2 
Jun 17 22:57:10 winetserv NetworkManager: <info>  (eth3): bringing up device. 
Jun 17 22:57:10 winetserv NetworkManager: <info>  (eth3): preparing device. 
Jun 17 22:57:10 winetserv NetworkManager: <info>  (eth3): deactivating device (reason: 2). 
Jun 17 22:57:10 winetserv NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Jun 17 22:57:10 winetserv NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Jun 17 22:57:10 winetserv NetworkManager: <info>  (eth2): device state change: 1 -> 2 
Jun 17 22:57:10 winetserv NetworkManager: <info>  (eth2): bringing up device. 
Jun 17 22:57:10 winetserv NetworkManager: <info>  (eth2): preparing device. 
Jun 17 22:57:10 winetserv NetworkManager: <info>  (eth2): deactivating device (reason: 2). 
Jun 17 22:57:10 winetserv NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Jun 17 22:57:10 winetserv nm-system-settings: Added default wired connection 'Auto eth2' for /org/freedesktop/Hal/devices/net_00_02_44_6d_fc_64
Jun 17 22:57:10 winetserv NetworkManager: <info>  (eth1): device state change: 1 -> 2 
Jun 17 22:57:10 winetserv NetworkManager: <info>  (eth1): bringing up device. 
Jun 17 22:57:10 winetserv NetworkManager: <info>  (eth1): preparing device. 
Jun 17 22:57:10 winetserv NetworkManager: <info>  (eth1): deactivating device (reason: 2). 
Jun 17 22:57:10 winetserv NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Jun 17 22:57:10 winetserv NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Jun 17 22:57:10 winetserv NetworkManager: <info>  (eth0): bringing up device. 
Jun 17 22:57:10 winetserv NetworkManager: <info>  (eth0): preparing device. 
Jun 17 22:57:10 winetserv NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Jun 17 22:57:10 winetserv NetworkManager: <info>  (eth1): carrier now ON (device state 2) 
Jun 17 22:57:10 winetserv NetworkManager: <info>  (eth1): device state change: 2 -> 3 
Jun 17 22:57:10 winetserv NetworkManager: <info>  Activation (eth1) starting connection 'Auto eth1' 
Jun 17 22:57:10 winetserv NetworkManager: <info>  (eth1): device state change: 3 -> 4 
Jun 17 22:57:10 winetserv NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jun 17 22:57:10 winetserv nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_02_44_73_e7_e3
Jun 17 22:57:10 winetserv NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jun 17 22:57:10 winetserv NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jun 17 22:57:10 winetserv NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jun 17 22:57:10 winetserv NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jun 17 22:57:10 winetserv NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Jun 17 22:57:10 winetserv NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Jun 17 22:57:10 winetserv NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Jun 17 22:57:10 winetserv NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jun 17 22:57:10 winetserv NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Jun 17 22:57:10 winetserv NetworkManager: <info>  (eth1): device state change: 5 -> 7 
Jun 17 22:57:10 winetserv NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Jun 17 22:57:10 winetserv NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Jun 17 22:57:10 winetserv NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Jun 17 22:57:10 winetserv nm-system-settings: Added default wired connection 'Auto eth3' for /org/freedesktop/Hal/devices/net_00_02_44_87_69_0d
Jun 17 22:57:10 winetserv NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jun 17 22:57:10 winetserv NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Jun 17 22:57:10 winetserv NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Jun 17 22:57:10 winetserv avahi-daemon[2985]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.1.
Jun 17 22:57:10 winetserv avahi-daemon[2985]: New relevant interface eth1.IPv4 for mDNS.
Jun 17 22:57:10 winetserv avahi-daemon[2985]: Registering new address record for 192.168.0.1 on eth1.IPv4.
Jun 17 22:57:11 winetserv NetworkManager: <info>  (eth1): device state change: 7 -> 8 
Jun 17 22:57:11 winetserv NetworkManager: <info>  Policy set 'Auto eth1' (eth1) as default for routing and DNS. 
Jun 17 22:57:11 winetserv NetworkManager: <info>  Activation (eth1) successful, device activated. 
Jun 17 22:57:11 winetserv NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Jun 17 22:57:11 winetserv mysqld[3261]: 090617 22:57:11  InnoDB: Shutdown completed; log sequence number 0 43655
Jun 17 22:57:11 winetserv mysqld[3261]: 090617 22:57:11 [Note] /usr/sbin/mysqld: Shutdown complete
Jun 17 22:57:11 winetserv mysqld[3261]: 
Jun 17 22:57:11 winetserv mysqld_safe[3427]: ended
Jun 17 22:57:11 winetserv avahi-daemon[2985]: Registering new address record for fe80::202:44ff:fe88:746b on eth1.*.
Jun 17 22:57:14 winetserv ntpdate[3494]: adjust time server 91.189.94.4 offset -0.343347 sec
Jun 17 22:57:22 winetserv /etc/init.d/mysql[3737]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Jun 17 22:57:22 winetserv /etc/init.d/mysql[3737]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Jun 17 22:57:22 winetserv /etc/init.d/mysql[3737]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Jun 17 22:57:22 winetserv /etc/init.d/mysql[3737]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
```there are slight differences between the last log i posted before and this one, that is some of mysqld still executed before networkmanager register ip address and the rest get executed after the ip has been registered, where it is still failed, because mysqld is already failed attempted to open port of the ip address.
is there something i miss?

---

### Post by Polaris96 on 2009-06-18
If you were in rcs.d you should've been able to nip that problem.  There is a pre-init process called upstart.  I don't know enough enough about it to advise you, but maybe you can pursue that avenue.  

I only know that, on modern kernels, upstart calls init.d, so if there's some call for mysql in either the kernel execution or the upstart process, it would pre-empt even rcs.d.

I'm sorry but I don't know how to help, anymore.  Good luck and please post the answer when you find it.

---

### Post by soulhealer on 2009-06-19
i couldn't find any solution for this yet.
so, rather than using 127.0.0.1 as mysql host, i use 0.0.0.0 which would allow me to remote mysql database from the network. this is the last resort that i can think of at the moment, because it is dangerous, since it is open to all network i have on my system.

---

