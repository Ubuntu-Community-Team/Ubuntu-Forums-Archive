---
title: "saned will not start"
date: 2009-01-09
forum: Desktop Environments
---

### Post by bluewind on 2009-01-09
Using Ubuntu 8.10 on my desktop PC (kernel 2.6.27-9-generic).
I have an HP Photosmart 5280 connected to this PC. Both printing and scanning work fine locally, but I want other machines to print and scan over my LAN.

Distant printing works fine, but not distant scanning : the saned daemon is unable to start.

If an attempt is made through xinetd, this is what can be found in syslog :
>  xinetd[5438]: added service sane-port [file=/etc/inetd.conf] [line=1]
 xinetd[5438]: bind failed (Address already in use (errno = 98)). service = sane-port
 xinetd[5438]: Service sane-port failed to start and is deactivated.

If saned is started directly in debug mode, the result is the same :
> [saned] main: starting debug mode (level 50)
[saned] main: trying to get port for service `sane-port' (getaddrinfo)
[saned] main: [0] socket () using IPv6
[saned] main: [0] setsockopt ()
[saned] main: [0] bind () to port 6566
[saned] main: [0] listen ()
[saned] main: [1] socket () using IPv4
[saned] main: [1] setsockopt ()
[saned] main: [1] bind () to port 6566
[saned] main: [1] bind failed: Address already in use
[saned] main: waiting for control connection

However  ```
netstat -nap | grep 6566
``` gives nothing which seems to indicate that the port is not in use. However, I note that bind seemed to work using IPv6. Is that what is preventing it to work using IPv4 ? And if that is the case how could I prevent it to try using IPv6 ?


This is the config file I have for sane in xinetd.d
> service sane-port
{
socket_type = stream
server = /usr/sbin/saned
protocol = tcp
port = 6566
user = saned
wait = no
disable = no
}


Also, the necessary line about sane-port (tcp at port 6566) exists in /etc/services and finally saned is a member of group scanner.

Can anybody help ?

---

### Post by bluewind on 2009-01-10
No idea at all ?

---

### Post by Balle-Larsen on 2009-02-08
I have a similar problem running with openbsd-inetd and user saned
If you set it up to run as user root in /etc/inet.conf it works or if you run e.g. saned -d5 as root on the server (with inetd stopped).
I am not proposing you to run saned as root, only stating that there must be a protection problem somewhere in the system.

---

### Post by bluewind on 2009-02-11
I had tried running it as root and also directly without inetd. I still had the same error. For some reason, the port that saned wants to use seems to be already occupied although it is not really the case.

But, by chancee I found a solution which bypasses saned completely. It means using Scanner Server, an application working through http. See
[ Linux Scanner Server ](http://scannerserver.online02.com/node/1)
And by the way, using the http port instead of opening an additional one is an additional advantage.

---

