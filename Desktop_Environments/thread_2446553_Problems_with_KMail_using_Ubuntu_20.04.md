---
title: "Problems with KMail using Ubuntu 20.04"
date: 2020-07-02
forum: Desktop Environments
---

### Post by davidcbryant on 2020-07-02
Hi! I've been using Ubuntu 10 (Bionic Beaver)  for about a year. It's generally been pretty well-behaved -- I set up an Ubuntu One account last summer, but I haven't had any questions until now. Oh, yeah. A word about my hardware. DELL XPS 8930 with Intel i7 9700 cpu (3 GHz) and 16 GB RAM. Connected (via ethernet) to a Netgear router (R6400), which is in turn connected via ethernet to a fiber-optic cable connecting my house with my ISP. Very good connectivity -- it tests out at about 225 Mbps in both directions.

This morning I decided to upgrade to "Focal Fossa" 20.04. That all went pretty smoothly, although it took a bit longer than I expected (about 1 hour 10 minutes, according to the "history.log" file). But now I have a problem.

I use KDE's KMail program to download and save my email. I have multiple email accounts, but two of them account for most of the traffic. Everything had been working well under 18.04. But now that I have upgraded my system, KMail is refusing to talk to one of my two main email accounts. KMail says "Unable to login to the server pop.gvtc.com.&#8232;Your POP3 server claims to support TLS but negotiation was unsuccessful.&#8232;You can disable TLS in the POP account settings dialog."

Now I have eight different Linux systems installed on my hard disk, and KMail is operational on five of them. The Ubuntu instance of KMail (5.13.3) is the only one issuing this message -- the other four work just fine. And Ubuntu was working OK yesterday. The problem arose as a result of the upgrade. I don't want to turn Starttls functionality off ... email encryption during transmission is a good idea. But just to test the connection, I told KMail to use "None" for encryption. I got the same error message -- I can't fetch my mail in an unencrypted mode, either (I always use POP3, not IMAP).

Has anyone else run into this problem? It certainly looks like a bug in KMail 5.13.3, to me. I ran a "Hardenize" report ([https://www.hardenize.com/](https://www.hardenize.com/)) against my isp's POP3 server just to be sure. They're supporting TLS 1.2, TLS 1.1, TLS 1.0, and SSL 3.0. TLS 1.0 and SSL 3.0 are deprecated, but that ought not cause KMail to fail. "Hardenize" does complain about a less than optimal cipher-suite configuration for TLS 1.2, but again, KMail ought to make the connection.

I would appreciate anybody's help and advice. If it's a bug, should I report it to the Ubuntu package managers? Or does it make more sense to report it to the KDE guys? Thanks!

---

### Post by davidcbryant on 2020-07-03
Well, this is weird. When I booted back into Ubuntu 20.04 this morning, KMail worked just fine. I guess the new system just hiccoughed, or something. Sorry to bother y'all.

David Bryant
Canyon Lake, Texas

---

