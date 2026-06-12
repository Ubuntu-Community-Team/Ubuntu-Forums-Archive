---
title: "Upgrade to KDE 3.5.3 =&gt; cannot logon to X"
date: 2006-06-24
forum: Desktop Environments
---

### Post by peholmst on 2006-06-24
Hello!

Last night I upgraded my Kubuntu 6.06 to KDE 3.5.3. After an Xserver-reboot I get the new login screen (without borders around the input boxes), but when I try to log on I get thrown back to the logon screen all the time, with the following message in .xsession-errors:

Xsession: X session created for petter at (date)
open: Permission denied

In xorg.log there are complaints about not being able to read the security policy file /etc/X11/sserver/SecurityPolicy (no such file exists on my system) and a bunch of "No matching visual for __GLcontextMode iwht visual class......"

I'm using the 64-bit version of Kubuntu on a HP zv6000 with the latest fglrx-driver (seems to be working better than the previous versions, but still causes a black screen forcing a hard reset every now and then, when will they get this fixed I wounder???).

Any clues would be appreciated,

-Petter-

---

### Post by peholmst on 2006-06-24
Problem solved, something had messed up the permissions on /tmp.

-Petter-

---

