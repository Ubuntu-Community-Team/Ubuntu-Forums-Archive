---
title: "vpnc works in hardy but not intrepid"
date: 2009-02-02
forum: General Help
---

### Post by mikelanc on 2009-02-02
Summary: For me, vpnc works in hardy but not intrepid.  
I use the same config file and desktop machine with 8.04 installed and vpnc works.  I've upgraded and fresh installed to 8.10 and vpnc errors with vpnc: no response from target.
Things I've tried:
From hardy I've configure sources.list to intrepid and upgraded vpnc and dependencies to intrepid versions and vpnc continues to work.
From intrepid I've downgraded vpnc and kernel to hardy versions and vpnc continues to fail.
All firewalls disabled.
I've tried things like disabling the new network-manager but that makes no difference.  
I've copied the libraries returned by ldd from a hardy installation to a separate dir and forced the intrepid vpnc to use these libs and it still fails.
tcpdump shows nothing is returned but it's a local issue as it works from hardy.

Anyone seen this behaviour?  What else can I try?
Thanks,
Mike

---

### Post by cmnorton on 2009-02-03
KVPNC does not work properly in Ubuntu 8.10, although it does connect. I installed it and the necessary KDE libraries to allow it to work in Gnome. The problem I encountered was the VPN would connect, bit it would not disconnect. 

KVPNC works fine in Kubuntu 8.04. I wanted an LTS version running on my workstation at work, and I am not likely to change that until the next Kubuntu LTS.

I am a subscriber to several KNetworkManager bugs. All I can suggest is subscribe to one or more of them and wait.

[https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/151867](https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/151867)
[https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/134547](https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/134547)
[https://bugs.launchpad.net/ubuntu/+source/kvpnc/+bug/289463](https://bugs.launchpad.net/ubuntu/+source/kvpnc/+bug/289463)

In re-reading your post, I cannot tell which method you are using to connect. I have always wimped out and used Network Manager or KVPNC. KVPNC and pptpconfig have nice debug logging, which could help you further.

---

### Post by mikelanc on 2009-02-03
My connection method is just on the command line through vpnc.  I've also tried using kvpnc which just calls vpnc so gives the same results.
$ sudo vpnc
[sudo] password for mikel:
Enter password for mikel@{deleted IP address}:
vpnc: no response from target

This is my config file.  As you can see I've tried lots of other settings collected from this and other forums.
$ cat /etc/vpnc/default.conf
IPSec gateway {deleted IP address}
IPSec ID {deleted user}
IPSec secret {deleted secret}
Xauth username {deleted username}
#IKE Authmode psk
#IKE DH Group dh2
#NAT Traversal Mode cisco-udp
#DPD idle timeout (our side) 0
#Local Port 10000
#AuthType 5

---

