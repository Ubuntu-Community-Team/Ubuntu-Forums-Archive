---
title: "Problem with Scrollkeeper?"
date: 2006-06-02
forum: Desktop Environments
---

### Post by Maupertus on 2006-06-02
When I try to install the updates that are available via the Update Manager, I get the following message:

[i]"Only one software management tool is allowed to run at the same time

Please close the other application e.g. 'aptitude' or 'Synaptic' first."[/i]

As I'm not using synaptic or aptitude at the moment I was wondering what could be the problem, so I ran Synaptic and got:

*"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "*

AHA! So that is the problem! And after running the command I see that indeed apparantly a scrollkeeper-update has had a problem. The problem is that nothing happens now and after half an hour of processor grinding I get this message:

[i]Setting up scrollkeeper (0.3.14-11ubuntu6) ...
Rebuilding the database. This may take some time.
dpkg: error processing scrollkeeper (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Setting up ubuntu-artwork (28) ...

dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured"[/i]

What is the problem and how can I solve it? Or better, as I know what the problem is, what causes this problem?

---

