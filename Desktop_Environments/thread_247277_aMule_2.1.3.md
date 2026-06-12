---
title: "aMule 2.1.3"
date: 2006-08-30
forum: Desktop Environments
---

### Post by Jonathan Métillon on 2006-08-30
Hi,

I'm having some difficulties connecting to eDonkey servers with *2.1.0-1ubuntu1 (dapper).*

My TCP/UDP ports are ok. The [TCP/UDP Port Connection Tester]("http://www.amule.org/testport.php") says that I should be able to use the ED2K P2P service.

However, the majority of servers time out when I try to connect to them. And when I'm lucky enough to connect, the transfers are very rare and slow.

It's very weird because some weeks ago it was very very fast and I could connect to any server I want within 1 second! I changed nothing in the meantime.

Someone in #amule said that *"distros don't upgrade the versions of packages in their released distros for anything but security fixes. Problem with amule is that server protocol may change over time and newer server versions won't let you in with an old client..."*

He suggested that I update aMule. Indeed the [official site]("http://www.amule.org/") distributes version 2.1.3 and only 2.1.0 is avaiable from Synaptic.

According to [this one,]("http://forum.amule.org/thread.php?threadid=10306") I added the *aMule 2.1.3 for Ubuntu Dapper i386 (testing)* repository and retrieved the public key.

Now *aMule 2.1.3-1ubuntu0-1 (twemu.no-ip.org)* shows up in Synaptic and when I try to install it, it says: *"Depends: libcrypto++5.2c2  but it is not installable".*

I have libcrypto++5.2c2a installed. What should I do?

---

### Post by Jonathan Métillon on 2006-09-18
I'm now [back to aMule 2.1.0]("http://ubuntuforums.org/showthread.php?p=1468275") and I'm still Low-ID. aMule log says:

```
2006-09-18 22:36:58:  - This is aMule 2.1.0 using wxGTK2 v2.6.1 (Unicoded) based on eMule.
2006-09-18 22:36:58:    Running on Linux 2.6.15-26-386 i686
...
2006-09-18 22:36:58: External connections disabled in config file
...
2006-09-18 17:03:22: Servers: Connected
2006-09-18 17:03:22: Connection established on: !-= www.FreeSexBay.com =-!
2006-09-18 17:03:22: WARNING: You have recieved Low-ID!
2006-09-18 17:03:22: 	Most likely this is because you're behind a firewall or router.
2006-09-18 17:03:22: 	For more information, please refer to http://wiki.amule.org
```

But still, the [TCP/UDP Port Connection Tester]("http://www.amule.org/testport.php") says **Success The TCP port 8459 is available.**

In *Preferences > Connection* I've set 8459 as *Standard client TCP Port* and 55492 as *Extended client UDP Port* and *disable* in unchecked. And *UDP Port for extended server requests* uses 8462 (TCP+3).

These 3 ports are forwarded to my fixed IP address by my wireless broadband router (Linksys WRT54G).

What did I forget? Is there another port to open? Or maybe it's my provider ([free.fr]("http://adsl.free.fr/")) is blocking something? Or should I really update aMule to 2.1.3?

Thank you for your time! O:)

---

