---
title: "GnomeBoy Advance error:"
date: 2005-12-05
forum: Gaming &amp; Leisure
---

### Post by Jujimufu on 2005-12-05
Hi, I've installed visualboy and gnomeboy advance - but whenever I try to change any preferences in gnomeboy I get this error readout:

> 
me@dhcppc:~$ sudo su
root@dhcppc:/home/hawaii# gnomeboyadvance

(GnomeBoyAdvance:29090): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
 is not a directory.
*** glibc detected *** free(): invalid pointer: 0xb7997580 ***


Can anybody help me?  I really want to play these games. :cry:

---

### Post by daveg on 2005-12-07
How come you're trying to run it as root? What happens when you run it with your normal user account?

I downloaded the gnomeboyadvance deb for ubuntu from [here]("http://developer.berlios.de/projects/gnomeboyadvance/") and it worked without any hassles.

Edit: I take that back. I see what you mean. I get it when I try to set the roms directory (I ended up typing the path to that directory instead of browsing) Perhaps a bug needs to be [filed with the project]("http://developer.berlios.de/bugs/?group_id=1650")

---

### Post by Jujimufu on 2005-12-07
Yes, but I don't want to create a login just to submit that bug.  

 I just found a work- around.  TYPE in the directory location instead of browsing for it.  Solves the problem, but they should still really look into fixing it.

---

### Post by daveg on 2005-12-07
[QUOTE=Jujimufu]Yes, but I don't want to create a login just to submit that bug.  
<snip>
Solves the problem, but they should still really look into fixing it.[/QUOTE]

If nobody submits a bug, how are they going to know about it?

[QUOTE=Jujimufu]I just found a work- around.  TYPE in the directory location instead of browsing for it.[/QUOTE]If you read my reply, you'd see that that's what I did to work around it.

---

