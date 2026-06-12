---
title: "live 9.04 nautilus crashes"
date: 2009-04-23
forum: General Help
---

### Post by BennyLZ on 2009-04-23
Hi,
I tried today the jaunty live CD. All works but nautilus. :confused:
It doesn't start when I launch the live, and It crashes when I try to start it from terminal. I tried with both "nautilus" and "sudo nautilus".

help!

---

### Post by Peter09 on 2009-04-23
When started from a terminal what errors are you getting (in the terminal after the crash). Can you paste them here?

---

### Post by drs305 on 2009-04-23
Try "nautilus --browser" just to see if it works that way. And as was mentioned, please give us the error messages.

Also, when you use root nautilus, use "gksudo nautilus" rather than "sudo" since it is a graphical app.
[_http://www.psychocats.net/ubuntu/graphicalsudo_]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by BennyLZ on 2009-04-23
There's a bug in libbrasero-media*

here there's the error message:
> sorry, the program "nautilus" closed unexpectedly.
your computer does not have enough free memory to automatically analyze the problem and send a report to the developers
(I've 1GB ram used for the 20/25%)

and I've got this line in syslog:
> ubuntu kernel: [350.087084] nautilus [5956] segfault at 9750008 ip b62187dd sp b60fefc0 **error 4 in libbrasero-media.so.0.1.1** [b653e000+1e000]

**If I uninstall libbrasero-media* (and brasero), nautilus works!**

What can I do?

PS: I tried the same live cd in my brother's PC, and both brasero and nautilus work...

---

### Post by drs305 on 2009-04-23
**libbrasero-media** is used by the brasero cd burning app. You can uninstall brasero and it  removes the offending library. There are other good cd burners, such as k3b, although that particular one would require installing quite a few additional libraries.

Just pick another cd burning app until the bug is fixed.  Note: I have 64-bit jaunty and do not experience this bug with brasero. My version of libbrasero is 2.26.0-0ubuntu3.

---

### Post by BennyLZ on 2009-04-23
I downgraded brasero to the preview version (0.9.1).
It still uses libbrasero-media, but it works.
I will use this version until the bug is fixed.

EDIT: After installing Jaunty, both nautilus and brasero works... so there was a problem limited to the live cd.

---

### Post by steen on 2009-04-25
I can confirm the OP's finding. Jaunty 9.04 x86 Nautilus bug with libbrasero-media0. Both live CD & install are affected. Removal of Brasero & lib solves the problem.

---

### Post by Odd_sam on 2009-04-27
I expierenced the same thing however Installation fixed this issue and a seg fault only occured in the live cd. Will there be a fixed iso released for this or will I have to use the 8.10 Live CD until 9.10 comes out.

---

### Post by rip_it on 2009-04-27
I ran into the same thing with Brasero cd burner.  It starting having segmentation faults yesterday, prevented me from watching Videos, accessing Documents or anything in the Places Menu. Caused a few more problems that I dont remember right now.  Fix was to uninstall Brasero. Contained two files.  Everything is back to normal.  Thanks whoever mentioned that above.

---

