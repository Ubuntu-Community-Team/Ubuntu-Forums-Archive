---
title: "nxserver default font 'fixed' possible solution."
date: 2006-11-02
forum: Desktop Environments
---

### Post by this on 2006-11-02
Since I upgraded to Edgy I have been unable to long into my box at home from work via NX.

After banging my head against this problem for a good few hours ](*,) (and reading some related threads on here) I think I may have come across the solution.

You may not need to do all of these steps but it shouldn't hurt you to repeat them.

[INDENT]sudo apt-get install xfs
sudo apt-get install --reinstall xfonts-base
[/INDENT]

I didn't seem to have xfs installed.

Now in /usr/NX/etc/node.cfg locate the line:

[INDENT]#AGENT_FONT_SERVER = "unix/:7100"[/INDENT]

and uncomment it.

Worked for me, hopefuly it will for someone else.

---

### Post by Outtascope on 2008-01-13
Thanks for that post, saved me a bunch of time. 

Though it should be obvious, it may be worth pointing out that the install is on the server machine.

On my Debian Etch server I used the following command:

[INDENT]apt-get install xfs xfonts-100dpi xfonts-75dpi xfonts-base xfonts-scalable
[/INDENT]

This got me past the following error and everything works perfectly now:

[INDENT]ERROR: Error when monitoring session: Could not open default font 'fixed' 'NXSessionMonitor::__setSessionStatus'[/INDENT]

Thanks again!
:guitar:

---

