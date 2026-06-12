---
title: "Installing Pydev for eclipse throws error"
date: 2009-12-29
forum: Desktop Environments
---

### Post by sridharpandu on 2009-12-29
I installed Eclipse using the Synaptic Package Manager. After which I started Eclipse clicked on Help|Install New software and entered the Pydev repositories. I clicked the Pydev for Eclipse from the list of software and clicked "Next". Eclipse displayed the license information at which point I accepted the terms and clicked "Next". During install I get the following error.

------------------------------------------------------------------------------------------------------
An error occurred while installing the items

  session context was:(profile=PlatformProfile, phase=org.eclipse.equinox.internal.provisional.p2.engine.phases.Install, operand=null --> [R]org.eclipse.ant.ui 3.4.1.v20090901_r351, action=org.eclipse.equinox.internal.p2.touchpoint.eclipse.actions.InstallBundleAction).
  The artifact file for osgi.bundle,org.eclipse.ant.ui,3.4.1.v20090901_r351 was not found.
------------------------------------------------------------------------------------------------------

A point to note is that I am not logged in as "su". How do I tell eclipse to ask for a root password. Could this be a reason.

Thanks in advance.

Best regards

Sridhar Pandurangiah

---

### Post by pjari on 2009-12-30
Hi Sridhar,

Yes, this was my error as well. What I did to resolve this was simply:
[LIST=1]
[*]sudo eclipse
[*]Add PyDev information under Help | Install New Software (add [http://pydev.org/updates](http://pydev.org/updates))
[*]complete the install, and restart eclipse (this time as myself)
[/LIST]

This worked flawlessly for me. Good luck.

Paul

---

### Post by sridharpandu on 2009-12-30
Paul

Thanks it works.

Best regards

Sridhar Pandurangiah

---

