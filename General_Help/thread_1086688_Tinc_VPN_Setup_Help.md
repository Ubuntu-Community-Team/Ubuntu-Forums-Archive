---
title: "Tinc VPN Setup Help"
date: 2009-03-04
forum: General Help
---

### Post by HornedBeast on 2009-03-04
Hello,

I am trying to use Tinc to setup a VPN between many different clients.

I have tried for days on end with no success on this, so I thought I would post it here and see if someone can help me at all.

**Here's the scenario:**


I have 1 PC with a Static IP/Domain (a dyndns.org account - myserver.homeip.net) connected to a router, which in turn is the gateway to the internet. It also has a static local IP (192.168.1.2). I will call this the "server" from now on.

To this, I wish to connect multiple client machines. These clients do not have static local IP's and do not have static internet IP's either (various locations around the globe). When the clients connect to the VPN, I want them to get an address from the pool of 192.168.2.* - up to as many as is needed (up to 8 machines at once perhaps). These IP's could also be static. So, Client1 could have 192.168.2.1, Client 2 could have 192.168.2.2, Client 3 could have 192.168.2.3 for example. The clients will also be standalone machines, and should not grant access to any other services on their own local networks they reside on.

What I would like to do is be able to use the server machine as a way of authenticating the other clients, but then have the clients only talk to each other in a big mesh - rather than using all the bandwidth of the server only. So, Client's 1, 2 and 3 would all have direct links with each other once they have authenticated against the main host.

However, I understand this is difficult as their IPs will change at varying times.


**The outcome:**

Clients authenticate with their keys against the master set of keys on the server. Once logged in, they can then see all the services of the other clients also connected to the network. So, if Client1 was running Windows and has folder sharing enabled, and Client 2 has a folder shared, they should be able to see eachothers shares. If client 3 connects, but has no shares, it should still be able to see both Client1 and Client2's shares and use them accordingly - with traffic going only between the required clients and NOT the server (as it only has a limited pipe.


**The problems:**


The system will need to be key based. All the keys for all the clients will reside on the server inside /tinc/hosts/ and the each individual client will have that very same key. But the problem with having all the keys on all the clients is that their IP's change, so I need to find a centralized way of getting all the clients to find out where each other is. I believe the external IP's of the machines are normally stored inside this key file, but since they have dynamic keys, it causes problems.

I assumed you would only need to have inside each client host file something like:

"ConnectTo = server
*KeyStuff*"

And the server would do the rest for me perhaps?

Can anyone help me with this scenario at all?

I was led to believe Tinc was designed from the ground up to support this type of infrastructure. I read this in the man pages:

```
TunnelServer = yes | no (no) [experimental]
             When this option is enabled tinc will no longer forward informa&#8208;

             tion between other tinc daemons, and will only allow nodes and
             subnets on the VPN which are present in the
             /etc/tinc/NETNAME/hosts/ directory.
```

So, if this was set to No (which it is by fault for each client I guess), does this not suggest that Tinc forwards information about other clients, to other clients on the VPN?

```
IndirectData = yes | no (no)
             This option specifies whether other tinc daemons besides the one
             you specified with ConnectTo can make a direct connection to you.
             This is especially useful if you are behind a firewall and it is

             impossible to make a connection from the outside to your tinc
             daemon.  Otherwise, it is best to leave this option out or set it
             to no.
```

And this option seems to suggest things related to my scenario.

Anyway, I have said enough I think.

Please let me know if I have explained this clearly enough and / or this is possible with Tinc, or any other VPN solution.

Any help regarding the above would be appreciated.

Thank-you in advance!

---

