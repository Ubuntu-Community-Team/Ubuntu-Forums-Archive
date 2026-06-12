---
title: "OpenSwan with XP client"
date: 2009-05-11
forum: General Help
---

### Post by murryahack on 2009-05-11
Hi ppl!

I've got a project to compare diffrent VPN-solutions (like openvpn and openswan) but I've ran into a few problems.. Right now there's only one though, and it's getting OpenSwan (running on ubuntu 8.10) to work with XP.

I think I've had every possible problem up untill where I am right now but i have been able to google the solution, but now I'm damn stuck :(


XP is giving me :

```
Error 792: The L2TP connetion attempt failed because security negotiation timed out.
```And ubuntu is giving me:

```

May 11 20:49:19 ubuntu-server pluto[5409]: "l2tp-X.509"[2] 192.168.58.148 #2: Main mode peer ID is ID_DER_ASN1_DN: 'C=SE, ST=Kalmar, O=HiK, CN=outside'
May 11 20:49:19 ubuntu-server pluto[5409]: "l2tp-X.509"[2] 192.168.58.148 #2: no crl from issuer "C=SE, ST=Kalmar, O=HiK, CN=server" found (strict=no)
May 11 20:49:19 ubuntu-server pluto[5409]: "l2tp-X.509"[2] 192.168.58.148 #2: no suitable connection for peer 'C=SE, ST=Kalmar, O=HiK, CN=outside'

```Here is my ipsec.conf:

```

# /etc/ipsec.conf - Openswan IPsec configuration file
# RCSID $Id: ipsec.conf.in,v 1.15.2.6 2006-10-19 03:49:46 paul Exp $

# This file:  /usr/share/doc/openswan/ipsec.conf-sample
#
# Manual:     ipsec.conf.5


version 2.0     # conforms to second version of ipsec.conf specification

# basic configuration
config setup
        # plutodebug / klipsdebug = "all", "none" or a combation from below:
        # "raw crypt parsing emitting control klips pfkey natt x509 private"
        # eg: plutodebug="control parsing"
        #
        # ONLY enable plutodebug=all or klipsdebug=all if you are a developer !!
        #
        # NAT-TRAVERSAL support, see README.NAT-Traversal
        nat_traversal=yes
        virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12:!192.168.1.0/24
        #
        # enable this if you see "failed to find any available worker"
        nhelpers=0

# Add connections here

# sample VPN connections, see /etc/ipsec.d/examples/


#Disable Opportunistic Encryption
include /etc/ipsec.d/examples/no_oe.conf
include /etc/ipsec.d/l2tp-cert.conf


```And here is my l2tp-cert.conf

```

conn l2tp-X.509
        #
        # Configuration for one user with any type of IPsec/L2TP client
        # including the updated Windows 2000/XP (MS KB Q818043), but
        # excluding the non-updated Windows 2000/XP.
        #
        #
        # Use a certificate. Disable Perfect Forward Secrecy.
        #
        authby=rsasig
        pfs=yes
        auto=add
        # we cannot rekey for %any, let client rekey
        rekey=no
        # Do not enable the line below. It is implicitely used, and
        # specifying it will currently break when using nat-t.
        #type=transport. See http://bugs.xelerance.com/view.php?id=466
        #
        left=%defaultroute
        leftsubnet=0.0.0.0/0.0.0.0
        # or you can use: left=YourIPAddress
        leftrsasigkey=%cert
        leftcert=/etc/ipsec.d/certs/outside.pem
        leftid="/C=SE/S=Kalmar/O=HiK/CN=server"
        leftprotoport=17/1701
        #
        # The remote user.
        #
        right=%any
        #rightca=%same
        rightrsasigkey=%cert
        # Using the magic port of "0" means "any one single port". This is
        # a work around required for Apple OSX clients that use a randomly
        # high port, but propose "0" instead of their port.
        rightprotoport=17/1701
        #rightsubnet=vhost:%priv,%no
        rightsubnet=0.0.0.0/0.0.0.0

```The Windows VPN-client is configured for L2TP IPsec VPN and I am allowing all Authentication methods atm..

OpenSwan starts without errors.. I just can't figure this out.

By the way, this ain't no NAT-T problem because both computers are on the same virtual switch (running the machines in VMware). And there is no firewall..

So if anyone has a solution to this I'd me thrilled..

Now I'm gonna sleep a few hours and hope for an epic answer ;-)

Murray

---

### Post by murryahack on 2009-05-14
So there is nobody who knows anything about this? ;(

---

