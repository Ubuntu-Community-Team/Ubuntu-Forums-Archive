---
title: "How to remove keyring?"
date: 2011-06-27
forum: Desktop Environments
---

### Post by Moozillaaa on 2011-06-27
Anyone know how to do this?

My log on is automatic, but wireless does not, so keyring removal is paramount.

---

### Post by lucazade on 2011-06-27
> **Moozillaaa said:**
> Anyone know how to do this?

My log on is automatic, but wireless does not, so keyring removal is paramount.

You have to set a blank password to your default keyring

open a terminal and launch:
seahorse

then from main window right click on default keyring and open 'Set password'.

in the next dialog change your password to a blank one, close everything and reboot.

---

### Post by Moozillaaa on 2011-06-27
[I]edit:
Looks like THAT problem was from bringing up a root-user shell. I re-opened seahorse as normal user, and THINK I got settings adjusted here. Now for the 293 updates to D/L & install !!![/I]



Thanks!

But alas - keyring sync problem. :confused:

So I'm doing a initial update fresh install 293 updates; maybe the KR bug is fixed (I know it's not fixed)...


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=196133&d=1309217498[/IMG]

---

### Post by lucazade on 2011-06-27
> **Moozillaaa said:**
> [I]edit:
Looks like THAT problem was from bringing up a root-user shell. I re-opened seahorse as normal user, and THINK I got settings adjusted here. Now for the 293 updates to D/L & install !!![/I]



Thanks!

But alas - keyring sync problem. :confused:

So I'm doing a initial update fresh install 293 updates; maybe the KR bug is fixed (I know it's not fixed)...


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=196133&d=1309217498[/IMG]

:)
I think you should launch seahorse as normal user and not as root because keyring for the network manager requires only normal user rights.

---

### Post by Moozillaaa on 2011-06-27
> **lucazade said:**
> :)
I think you should launch seahorse as normal user and not as root because keyring for the network manager requires only normal user rights.

Correct - I noted that in the edit.

Still waiting for initial updates/fresh install to complete, to re-boot, and see if I got it correct....

---

### Post by Moozillaaa on 2011-06-28
Worked - thanks!

---

