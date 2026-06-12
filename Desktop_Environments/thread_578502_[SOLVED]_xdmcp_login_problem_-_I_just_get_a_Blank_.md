---
title: "[SOLVED] xdmcp login problem - I just get a Blank Screen."
date: 2007-10-17
forum: Desktop Environments
---

### Post by applegrew on 2007-10-17
For the past 2 or 3 hours I have been trying to log into via XDMCP, trying different permutations like making the server loginto just the console mode, etc. The server (into which I intend to login) is a Ubuntu Fiesty system (uname -a output: Linux p4 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux). The client is a Kubuntu Feisty system (uname -a output: Linux applegrew 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux). **I have _of course enabled XDMCP_ from gdmsetup.**

When I press Alt+R at the login screen and type my server IP then my xserver re-starts (or probably a new xserver starts) and then I am taken to a blank screen which has just a cross as my curso, that's all and it stays there for eternity.

What's going on? Both my Client and Server are connected directly via a LAN cable and I can successfully access my server from the host using VNC.:confused:

---

### Post by applegrew on 2007-10-17
Forgot to add another thing. The Xserver or whoever is supposed to answer XDMCP login request is supposed to listen at port 177 (I can confirm this from the config file too /etc/X11/gdm/gdm.conf), but my portscan (from the client) shows that no such port is open! BTW  have not installed any firewall. Is Iptables blocking it?

---

### Post by applegrew on 2007-10-17
Just fixed i. :D Probably iptables was not allowing access to the 177 UDP and 6000 TCP ports. So, I installed firestarter and configured them and now it is working.

---

