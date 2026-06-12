---
title: "Ubuntu 8.10 slow Remote Desktop on LAN"
date: 2008-12-18
forum: General Help
---

### Post by SirGumps on 2008-12-18
I have Ubuntu 8.10 on my Studio 1735 laptop. It seems to run flawlessly except one issue:

Remote Desktop is slower than old lady with a broken hip running a marathon.

From my Windows XP desktop, I try to remote desktop to the Ubuntu 8.10 laptop via TightVNC for Windows and it's crawling. It takes almost 10 seconds just for the popup asking for the password to appear. Doing anything has major delays, regardless of the compression or how ugly (lowering quality) I make it.

Both computers are on a wired Gigabit LAN connection. The router is a DIR-655.

I just transfered a 1.4gb file at at roughly 50MB/sec, so the network connection is pretty decent.

Any ideas why the Ubuntu remote desktop is so damn slow?

---

### Post by SirGumps on 2008-12-19
Bumping. Anyone? - Also, is this the right forum?

---

### Post by den140 on 2008-12-26
Same situation here. 8.10. Sometimes take more than 60 seconds to respond to a mouse click. Local wifi network. Have tried Windows, OSX and Ubuntu clients.

---

### Post by HermanAB on 2008-12-26
On Linux systems, VNC is almost always the wrong solution.  Rather install OpenSSH server on Linux and connect from Windows using Xming and PuTTY.

That being said, the slowness is likely due to a misconfiguration in the authentication system.  You'll have to run a packet sniffer to figure it out, if you have the time to waste.

Cheers,

Herman

---

