---
title: "IP masquerading"
date: 2005-08-18
forum: Desktop Environments
---

### Post by kamiccolo on 2005-08-18
Is something like that possible? I don't feel good when I think of people who get my IP everywhere and try to access my computer.

---

### Post by invalid on 2005-08-18
Consider using a proxy.

Cheers,
Cb

---

### Post by TristanMike on 2005-08-18
kamiccolo, I saw people discussing this very same thing with commands over here...

[http://www.ubuntuforums.org/showthread.php?t=56927&highlight=masquerading](http://www.ubuntuforums.org/showthread.php?t=56927&highlight=masquerading)

Hope this helps  :)

---

### Post by kamiccolo on 2005-08-18
Hmmm. I need a bit more time to understand all this. As a German my English isn't as well as yours.
For better understanding: is the link you gave me really about hiding the own IP in the internet, so others can't see it?

I hope you now don't think that Germans aren't clever enough to understand an English text. ;-) It's like I would make a clown of myself.  :grin:

---

### Post by az on 2005-08-18
[QUOTE=kamiccolo]Hmmm. I need a bit more time to understand all this. As a German my English isn't as well as yours.
For better understanding: is the link you gave me really about hiding the own IP in the internet, so others can't see it?

I hope you now don't think that Germans aren't clever enough to understand an English text. ;-) It's like I would make a clown of myself.  :grin:[/QUOTE]


IP masquerading means internet connection sharing.  Basically, your computer is routing packets from one Network card to another (your computer must have two or more network cards to do this.)

What you are talking about is more like anonimity?

kurn@ubuntu:~$ apt-cache show anon-proxy
Package: anon-proxy
Priority: optional
Section: universe/web
Installed-Size: 312
Maintainer: David Spreen <netzwurm@debian.org>
Architecture: i386
Version: 00.02.39-3
Depends: debconf, libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:3.4.1-3), libssl0.9.7, libstdc++5 (>= 1:3.3.4-1), libxerces25
Suggests: mixmaster, tor, mixminion
Filename: pool/universe/a/anon-proxy/anon-proxy_00.02.39-3_i386.deb
Size: 125124
MD5sum: c16beb26a5d16e9d8fe2f88704878d4d
Description: Proxy to surf the web anonymously
 This package contains the JAP client which acts as a local proxy between
 your browser and the insecure Internet. All requests for web pages are
 handled by JAP and are encrypted several times. The encrypted messages
 are sent through a chain of intermediate servers (named Mixes) to the
 final destination on the Internet.
 .
 Multiple layers of encryption protect all messages. A Mix collects
 messages in a batch, totally changes their appearance (removes one
 layer of encryption) and forwards them all at the same time, but
 in a different order. An adversary may observe all communication links,
 however he cannot determine a relation between incoming and outgoing
 packets. A surfer remains anonymous within the group of all users
 of the service.
 .
 Demonstrably, the system protects your privacy as long as the Mix
 works correctly. Unfortunately nobody knows whether a certain Mix
 is actually trustworthy or not. Therefore we use a whole chain of
 Mixes. Each message passes through several Mixes and the entire chain
 of Mixes has to be corrupt to successfully observe the user's
 activities. The chaining effectively prevents single Mixes from
 observing. This is the meaning of strong anonymity: Even the
 anonymity service itself cannot spy on its users.
 .
 For further information see [http://anon.inf.tu-dresden.de/](http://anon.inf.tu-dresden.de/)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu




kurn@ubuntu:~$ apt-cache show tinyproxy
Package: tinyproxy
Priority: optional
Section: universe/net
Installed-Size: 236
Maintainer: Ed Boraas <ed@debian.org>
Architecture: i386
Version: 1.6.3-2
Depends: libc6 (>= 2.3.2.ds1-4), logrotate
Filename: pool/universe/t/tinyproxy/tinyproxy_1.6.3-2_i386.deb
Size: 67040
MD5sum: 734236bb7300921649e471f37a94ce0b
Description: A lightweight, non-caching, optionally anonymizing http proxy
 An anonymizing http proxy which is very light on system resources,
 ideal for smaller networks and similar situations where other proxies
 (such as Squid) may be overkill and/or a security risk. Tinyproxy can
 also be configured to anonymize http requests (allowing for exceptions
 on a per-header basis).
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

kurn@ubuntu:~$



Perhaps those two packages are what you want?

---

### Post by kamiccolo on 2005-08-19
That's exactly what I need. Thank you!

---

