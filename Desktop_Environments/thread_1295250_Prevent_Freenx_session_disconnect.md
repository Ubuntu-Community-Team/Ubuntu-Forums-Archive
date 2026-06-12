---
title: "Prevent Freenx session disconnect"
date: 2009-10-19
forum: Desktop Environments
---

### Post by yitzhakbg on 2009-10-19
No help so far. Here's a (hopefully) easier question:
nxclient uses configuration files with an ".nxs" extension in the .nx subdirectory. It is an XML file with keys and groups.
There must be additional keys which are configurable manually, but not through the GUI. I have not, for the life of me, been able to find documentation. One of them has to be the timeout session parameter (after all, there is a default value - around 30 sec.), which is passed to nxssh, the NX ssh client. How can I see the complete documentation, including those hidden parameters. What is the timeout key called??? How can it's value be changed. H E L P!!

Here's my original post:
We've got Freenx working nicely through NXClient.

Our problem is that we have to disconnect from the LAN in order to access the Internet. When we reconnect to the LAN, NX has to renegotiate the connection. The session itself is persistent. That's great, but the renegotiation takes a long time.

Question: Where is the timeout parameter which can extend the disconnect time? It apparently has nothing to do with SSH. I extended the ssh timeout, but to no avail.
Nomachine NX has a parameter called NodeResponseTimeout, but FreeNX does not. Is there a similar solution in FreeNX?
Thanks in Advance,
Yitzhak

---

