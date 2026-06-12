---
title: "Problems with vpnc"
date: 2005-12-28
forum: Desktop Environments
---

### Post by Balachmar on 2005-12-28
I want to logon to the network of my university using vpn.
I have distilled the information needed from a cisco profile.
And I have created a profile for vpnc.
So far so good.
But when I run vpnc I get the following error message:
willem@s000376:/etc$ sudo vpnc --debug /etc/vpnc/vpnc.conf
Enter password for s000376@131.155.14.99:
vpnc: quick mode response rejected: INVALID_PAYLOAD_TYPE
this means the concentrator did not like what we had to offer.
Possible reasons are:
  * concentrator configured to require a firewall
     this locks out even Cisco clients on any platform expect windows
     which is an obvious security improvment. There is no workaround (yet).
  * concentrator configured to require IP compression
     this is not yet supported by vpnc.
     Note: the Cisco Concentrator Documentation recommends against using
     compression, expect on low-bandwith (read: ISDN) links, because it
     uses much CPU-resources on the concentrator

What should I do to fix this?

---

### Post by ape on 2005-12-28
Try to  run vpnc with the --enable1des switch.

If this doesn't work, please run vpnc with the following switches and upload the output:

   vpnc --debug 2 --no-detach

Thanks!

---

### Post by Balachmar on 2005-12-29
[QUOTE=ape]Try to  run vpnc with the --enable1des switch.[/QUOTE]
Same thing... invalid payload.
[QUOTE=ape]
vpnc --debug 2 --no-detach
[/QUOTE]
vpnc version 0.3.3
S1
S2
S3
using interface vpnlink
S4
S4.1
S4.2
S4.3
S4.4
IKE SA selected psk+xauth-3des-md5
S4.5
NAT status: no NAT-T VID seen
S4.6
S5
S5.1
S5.2
S5.3
S5.4
Enter Username and Password.
S5.5
S5.2
S5.3
S5.6
S5.7
S6
got save password setting: 0
got 1 acls for split include
acl 0: addr: 131.155.0.0/255.255.0.0 (16), protocol: 0, sport: 0, dport: 0
got pfs setting: 0
Remote Application Version: Cisco Systems, Inc./VPN 3000 Concentrator Version 4.0.5.B built by vmurphy on Aug 27 2004 08:48:03
got address 131.155.212.206
S7
S7.1
S7.2
S7.3
S7.4
ignoring responder-lifetime notify
S7.3
S7.4
S7.5


---!!!!!!!!! entering phase2_fatal !!!!!!!!!---


vpnc: quick mode response rejected: INVALID_PAYLOAD_TYPE
this means the concentrator did not like what we had to offer.
Possible reasons are:
  * concentrator configured to require a firewall
     this locks out even Cisco clients on any platform expect windows
     which is an obvious security improvment. There is no workaround (yet).
  * concentrator configured to require IP compression
     this is not yet supported by vpnc.
     Note: the Cisco Concentrator Documentation recommends against using
     compression, expect on low-bandwith (read: ISDN) links, because it
     uses much CPU-resources on the concentrator

---

### Post by Balachmar on 2006-01-03
*kick*

---

### Post by Balachmar on 2006-01-09
* my weekly kick* this problem still exists... I even posted the requested information, there must be some people out there that use vpnc.... and can help me out...

---

### Post by Balachmar on 2006-01-15
* my weekly kick* this problem still exists... I even posted the requested information, there must be some people out there that use vpnc.... and can help me out...

---

### Post by cwaldbieser on 2006-01-15
[QUOTE=Balachmar]* my weekly kick* this problem still exists... I even posted the requested information, there must be some people out there that use vpnc.... and can help me out...[/QUOTE]
Have you tried any other Cisco VPN programs?

[http://www.cites.uiuc.edu/vpn/download-install.html]("http://www.cites.uiuc.edu/vpn/download-install.html")

I think the lack of responses to your problem is that Cisco VPN is a somewhat specialized knowledge area and your problem is somewhat obscure.  You might have some better luck asking on the networking forum.

---

### Post by nlvivar on 2006-08-15
Have you tried looking at this page?

[http://femto.cs.uiuc.edu/~sbond/vpnc/](http://femto.cs.uiuc.edu/~sbond/vpnc/)

Following his instructions, I was able to get VPNC up in about 30 minutes... and I'm a newbie, to boot.

Let us know about your results.

---

### Post by x64Jimbo on 2006-08-25
> **nlvivar said:**
> Have you tried looking at this page?

[http://femto.cs.uiuc.edu/~sbond/vpnc/](http://femto.cs.uiuc.edu/~sbond/vpnc/)

Following his instructions, I was able to get VPNC up in about 30 minutes... and I'm a newbie, to boot.

Let us know about your results.
I tried the instructions on that site you listed, but there doesn't seem to be a "console.apps" directory in my /etc/security. Can you detail how you did it?
Or could someone tell me another method to start vpnc without sudo? I've already tried adding vpnc to my sudoers file with visudo, but apparently the permissions are deeper seated than that one command, because it skips the root password, but still gets the Permission Denied error on opening port 500.

---

### Post by dheep on 2006-08-26
hi,

We have CISCO VPN concentrator 3000 in office. 
vpnc with the --enable-1des switch worked for me.
command used:-
[I]~$ sudo vpnc --enable-1des sifyadmin.conf
[/I]
kindly help on how to disconnect the vpn. 
tried using vpn-disconnect but the following is the error it gave

[I]~$ vpnc-disconnect
no vpnc found running[/I]

kindly advice how to disconnect the vpn.

---

