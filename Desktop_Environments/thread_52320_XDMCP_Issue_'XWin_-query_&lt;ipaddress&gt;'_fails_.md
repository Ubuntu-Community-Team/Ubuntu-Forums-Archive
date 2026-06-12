---
title: "XDMCP Issue: 'XWin -query &lt;ipaddress&gt;' fails to start gnome. Why?"
date: 2005-07-27
forum: Desktop Environments
---

### Post by OzPhoenix on 2005-07-27
The most easy way to establish an XDMCP connection on Windows is with XWin from cygwin (part of Xorg). All you need to do is type:

XWin -query <ipaddress>

I use this daily at work to connect to my solaris machines, not a single issue.

_**But on ubuntu I have a PROBLEM**_

I have read about other people having these problems, and even found an overly complicated guide in the Ubuntu Wiki on setting up cygwin to do XDMCP connections. But all this information is overly detailed when the fact of the matter is, you should only have to do the above command. NOTHING extra (oh, other than turn on XDMCP on your ubuntu machine).

So let me explain the situation, and then what I'm after.

**Problem Description**

Able to successfully connect via XDMCP (using the above command) to my ubuntu box. Prompted via GDM to authenticate, and am able to do this successfully. However then I'm presented with a full screen of the background colour for the desktop, and my pointer. It appears that Gnome fails to start.

(This is nothing new, everyone seems to be experiencing this.)

If however, you choose not to start Gnome but to start a failsafe xterm session (via the GDM login screen at login time), you will get the above but with the addition of the expected xterm window. So it purely seems to be an issue with starting Gnome.

**What I'm after**

One of three things:
1. Instructions of what I need to fix on my ubuntu box - as I believe the problem is there.
1.a. Or proof that for some bizare reason I have to do something other than the above command - but seeing this works with other XDMCP implementations I shouldn't have to
2. How I'd go about diagnosing this problem. Which log files to look at, etc.

Thank you for your time, I hope that someone out there can get this working for me and all the other ubuntu users having problems.

Cheers,
OP.

---

### Post by OzPhoenix on 2005-07-28
Please? Anyone?

Even information on where I'd find the shell script or whatever that is meant to start gome? Even where the gnome log files are.

Please help,
OP.

P.S. No, I don't want to use VNC as I like the speed of XDMCP sessions over VNC.

---

### Post by krish on 2005-08-16
OP,
  Enable port 16001 on the windows machine.  Open both TCP and UDP ports.  That should solve your problem.  Gnome wants the ESPEAKER default port to be open.

Siva.

---

### Post by OzPhoenix on 2005-08-16
Krish

Nice work. To try it quickly, I turned off the windows firewall and everything now works. Thanks heaps champ. (Now to go and do it properly.)

Do you know if/where I can turn off esound/espeaker?

Thanks,
OP.

---

### Post by OzPhoenix on 2006-04-25
Cool, just now finally got around to just adding the ports to Windows Firewall. All works like a charm.

Thanks again,
Oz.

---

