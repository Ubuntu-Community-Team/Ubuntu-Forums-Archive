---
title: "sane network scanning problem"
date: 2006-08-15
forum: Desktop Environments
---

### Post by fdimmling on 2006-08-15
In Breezy I had my scanner available over the network using saned. In Dapper I cannot get a connection. However the scanner is available locally on the machine it is attached to.
I have installed xinetd and edited hosts.allow to

ALL: .mylocalnet

and created a file sane in /etc/xinet.d

service sane-port
{
        disable = no
        socket_type = stream
        protocol = tcp
        wait = no
        user = saned <----------------- user and group must be root ----
        group = saned <----------------
        server = /usr/sbin/saned
}

In /etc/sane.d/saned.conf there is a line for every computer that should use the scanner, like

192.168.0.7

I can telnet to the server port 6566

causing saned to start (and quit after shutting down the telnet connection)

What's going wrong?

[see above: user and group in service sane-port must be root]

Friedrich, now =D>

---

