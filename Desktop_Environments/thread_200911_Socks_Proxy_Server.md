---
title: "Socks Proxy Server"
date: 2006-06-20
forum: Desktop Environments
---

### Post by Nomad64 on 2006-06-20
I am trying to setup a proxy server on a computer at my house for use, via Hamachi, outside of my house network.

I have installed the packages socks4-server and netkit-inetd to use a Socks4 server. I modified the configuration files as shown below:```
# /etc/sockd.conf
# Replace 'my.domain' below with your own domain name before using.
# Make sure you retain the leading period.

#deny   ALL  0.0.0.0            .my.domain  0.0.0.0
#permit .my.domain  0.0.0.0     ALL  0.0.0.0

# Allow hamachi clients to use the proxy, deny everyone else
permit 5.0.0.0 255.0.0.0
#deny 0.0.0.0 0.0.0.0
permit 0.0.0.0 0.0.0.0

```
```
#/etc/socks.conf
# socks configuration
#direct                  127.0.0.1       255.255.255.255
#direct                  10.7.10.255     255.255.255.0
sockd                   0.0.0.0         0.0.0.0
direct 192.168.0.0 255.255.255.0

```
```
#/etc/inetd.conf
ftp     stream  tcp     nowait  root    /usr/sbin/tcpd /usr/sbin/proftpd
#<off># netbios-ssn     stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/smbd
socks stream  tcp  nowait  nobody  /usr/sbin/sockd sockd

```

I then ran:```
sudo /etc/init.d/inetd reload
sudo /etc/init.d/inetd restart
```

I check the running processes, and I can see that the inet daemon is running, and a port scan of that computer reveals that port 1080 is open on that computer. However, when I put the proxy information into Firefox, and try to load google.com, it fails saying the connection was reset.

/var/log/syslog reveals:```
localhost sockd[8639]: error -- wrong version (0x47) from host 192.168.0.197
```

What the heck is going on here? Anyone have any suggestions as to how I can fix this?

---

### Post by lamego on 2006-06-21
Why are you using Socks4 instead of Socks5 ? Eventually Fireofox does not properly support Socks4 and that would explaing the daemon reporting a wrong version...

---

