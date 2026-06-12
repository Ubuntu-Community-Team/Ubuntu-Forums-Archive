---
title: "Securing my unbuntu box for my server"
date: 2006-09-07
forum: Desktop Environments
---

### Post by Mikeee on 2006-09-07
Hi all,

I have just installed a clean ubuntu desktop system. I want to code a server and run it from this system. The server will be multi-threaded to allow multiple clients to connect. Each client will have their own encrypted text file on my system which will contain their username and password to allow them to connect.

Obviously there are security issues I need to consider with running this. Can someone recommend what Id need to do to make my system as safe as possible?

I.E. What system logging should I use? Should I use strict IPTables? Is there away that I can only allow the server to write to the specific text files (the clients username and password files) and nothing else? Should I disable all other running services?

I am also developing the client that will connect to my server. Is there any security issues I should consider with the client?

Thanks for any help :-)

Oh btw, heres the output of when i nmap localhost. Let me know if theres anything else like this i can show you to help configuration

```

PORT      STATE SERVICE         VERSION
631/tcp   open  ipp             CUPS 1.1
32771/tcp open  sometimes-rpc5?
32772/tcp open  sometimes-rpc7?

```

---

### Post by TwoWordz on 2006-09-07
As always basic security practices should be applied.

Keep open ports to a minimum
Run the daemon with it's user account (no root)
chroot it
do not permit root to log into your application
consider using xinet.d

TW

---

