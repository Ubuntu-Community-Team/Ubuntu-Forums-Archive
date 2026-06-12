---
title: "can't start gdm after installing VMWare tools"
date: 2009-03-01
forum: General Help
---

### Post by valan on 2009-03-01
Hi there,
I'm killing myself right now. 
I'm a little new to this, but a quick learner. 
I'm running VMWare workstation 5.5 on WinXP. 
I upgraded my "browser appliance (ubuntu 5.10)" to 8.04 and it was working great.  So I figured I'd add/update the 'VMWare tools'.  Found bunch of great posts with instructions, all seemed to work fine, then I rebooted after the install and it went to the command line login, with the following message the to of the screen:

 PCI cannot allocate resource region 4

When I login, and try to run 'sudo gdm' I get the following:
Warning: GDM already running.  Aborting!

When I try 'startx' I get:
exec: 5: /usr/bin/X11/X: not found
giving up.
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error.

Any help would be greatly appreciated! I really don't want to re-install everything.  There has to be a way to fix this.

Cheers
-V

---

