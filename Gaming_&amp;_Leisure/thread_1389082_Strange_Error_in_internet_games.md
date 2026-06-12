---
title: "Strange Error in internet games"
date: 2010-01-23
forum: Gaming &amp; Leisure
---

### Post by 1337-1 on 2010-01-23
I've recently started getting my ubuntu desktop ready for gaming, and have discovered that there's an issue with the way the games...connect I guess?  Any server I join comes up with the following error in the console:

NET_SendPacket ERROR: Resource temporarily unavailable to 202.172.99.1:27048

And this just spams until the server boots me for various reasons.

I've only been able to test this with Tremulous and Quake Live, but the same error occurs.  Other games I attempt to test this with result in not actually finding any games to test it with.  I'd say that its probably the same issue though :D

I've never really had any issues with the internet before - once we had it working, it all worked fine.  Just now when I try and play games...it doesn't want to connect.

Anyone have any idea how to fix it?  Or even what's wrong?

---

### Post by tgeer43 on 2010-01-24
> **1337-1 said:**
> I've recently started getting my ubuntu desktop ready for gaming, and have discovered that there's an issue with the way the games...connect I guess?  Any server I join comes up with the following error in the console:

NET_SendPacket ERROR: Resource temporarily unavailable to 202.172.99.1:27048

And this just spams until the server boots me for various reasons.

I've only been able to test this with Tremulous and Quake Live, but the same error occurs.  Other games I attempt to test this with result in not actually finding any games to test it with.  I'd say that its probably the same issue though :D

I've never really had any issues with the internet before - once we had it working, it all worked fine.  Just now when I try and play games...it doesn't want to connect.

Anyone have any idea how to fix it?  Or even what's wrong?
Sounds like maybe a misconfiguration of your firewall/IP Tables. You may need to forward the appropriate port(s), 27048 in your example.

There are many good How-Tos on doing this. Just search these forums or google for "ubuntu port forwarding" and you should find what you are looking for very easily.

tgeer

---

