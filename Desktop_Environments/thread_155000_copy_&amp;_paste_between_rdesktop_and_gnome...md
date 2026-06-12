---
title: "copy &amp; paste between rdesktop and gnome..?"
date: 2006-04-04
forum: Desktop Environments
---

### Post by phrawzty on 2006-04-04
Hello all, long-time lurker, first-time poster.. :)

My problem is a simple one: i cannot seem to cut and paste text between rdesktop and the rest of the window manager.  I am running Ubuntu 5.10, using the included "Terminal Server Client", and connecting to a Windows Server 2003 SE machine.

Normally, i would just accept that this is a limitation of the software; however, i have seen a co-worker, running the freebsd port of rdesktop, and connecting to the same machine, cut and paste properly.

Furthermore, the rdesktop documentation suggests that it is entirely possible to cut and paste without any additional configuration.

What am i doing wrong here? :-?

---

### Post by xenmax on 2006-04-04
Could not believe it was not possible, so i tried it out. And like you said, whatever i tried, copying stuff from rdesktop was not availabe locally. 
Finally i found the answer - atleast one that works for me - while connecting, use RDPv5 as protocol, not just RDP. Now i can select text from my rdesktop and can paste in local machine using Middle mouse click or "Shift Insert"

Also, this clipboard business might be tricky. At work, i RDP to a windows server from a windows XP machine and sometimes copying text from a terminal opened using Exceed would not be available to local windows machine, unless i paste it in a text doc in remote desktop and then copy, now its available to local windows..
Now that i think, this might not be of concern to you, i guess this is specific to running linux apps from windows on RDP...

---

### Post by phrawzty on 2006-04-05
[QUOTE=xenmax]Finally i found the answer - atleast one that works for me - while connecting, use RDPv5 as protocol, not just RDP. Now i can select text from my rdesktop and can paste in local machine using Middle mouse click or "Shift Insert"[/QUOTE]

Setting the protocol to RDPv5 did the trick.  Good call, thanks!

---

