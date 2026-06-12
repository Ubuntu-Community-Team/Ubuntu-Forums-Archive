---
title: "All printing commands hang"
date: 2006-07-25
forum: Desktop Environments
---

### Post by ghotra on 2006-07-25
Hi, all printing commands are hanging. If I print from evince, gv, xpdf, etc...the program freezes. At the command line, programs like lp, lpq, lpr, lpstat, lpoptions all hang as well.

I have restarted my computer and this did not solve the problem.  I did not have this problem a couple hours ago when I was printing without problems (and I have not changed anything, that I am aware of since then).

My setup was fairly simple:

---/etc/cups/client.conf----
ServerName print.myserver.com

and then I set my default printer:
# lpoptions -d mydefaultprinter

After that, I was able to print...until it just recently stopped working.

Any ideas?

---

