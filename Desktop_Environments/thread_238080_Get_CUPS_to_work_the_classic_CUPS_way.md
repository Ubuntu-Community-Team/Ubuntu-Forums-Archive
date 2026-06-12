---
title: "Get CUPS to work the classic CUPS way?"
date: 2006-08-17
forum: Desktop Environments
---

### Post by kikinovak on 2006-08-17
Hi,

I'm an ex-long-time-Slacker recently converted to Ubuntu. I like it, but among the few things I don't quite appreciate is the horrible things the Ubuntu people did to CUPS.

Example: I want to setup a machine as a printer server. OK, so I install Ubuntu Desktop, my printer (a Brother-HL2030 laser printer) gets "recognized" as HL-2060 by gnome-cups-manager, click, OK. Now if I want to enable that printer on a remote machine, gnome-cups-manager, "detect LAN printer", click, OK.

Now... what if my printer server is a "headless" server, e. g. without X? In the olden Slack days, I only installed a minimal (as in: less than 300 MB) system with CUPS, edited cupsd.conf from scratch, allowed, say, 192.168.1.* for printing and the same for remote admin, and then, from any machine, I could open my admin interface with a web browser and administer things from there. That way, I didn't have to install a kitchen sink on my printer server, so any old battered Pentium I 90 MHz would do. With Ubuntu, no way to get the web interface work correctly.

Is there any HOWTO about getting CUPS to work in a classic CUPS way?

---

