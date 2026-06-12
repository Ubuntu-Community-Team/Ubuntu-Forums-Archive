---
title: "Programs shutting down/vanishing with 8.10"
date: 2008-11-06
forum: Desktop Environments
---

### Post by fenderuser on 2008-11-06
I have put this also in Installation & Upgrades but had no response and thought I would try here in case anyone has had a similar problem that I am unable to resolve, though thinking of trying a different distro, but hope it does not come to that.

Since upgrading from 8.04 to 8.10 I am having problems with running applications suddenly vanishing (shutting down) for no apparent reason. In particular, the problem occurs with Kompozer every time I use it and occasionally with OpenOffice Presentation.

When using Kompozer it will usually vanish/shut down with the first addition/insert of anything (eg an image). It suddenly disappears and is not running. I have checked (ps -aux) to see what processes are there, but Kompozer has gone.

A similar thing occasionally happens with Presentation, after some time it too will suddenly disappear/shut down.

I have run Kompozer through terminal, and when it 'crashes' I get an error message:
---------------------------------------------
pure virtual method called

terminate called without an active exception

Aborted
---------------------------------------------
Previously when running with 8.04 I had no problems whatsoever, only with the upgrade to 8.10 has this occurred.

Any suggestions/ideas?

---

### Post by jimwhitend on 2008-11-06
I have had the identical symptom in openoffice.org Writer. Never had it with 8.04.  FWIW.

Jim

---

### Post by fenderuser on 2008-11-07
> **jimwhitend said:**
> I have had the identical symptom in openoffice.org Writer. Never had it with 8.04.  FWIW.

Jim



Any idea how this gets reported as a possible bug? It does seem that it is 8.10 related.

Out of interest I thought I would install another disto. I chose Mint as it is very similar to Ubuntu. Installed it in virtualbox and ran it. Then installed Kompozer (where I have most of the problem). Using Mint Kompozer works fine, unlike Ubuntu 8.10.

---

### Post by crjackson on 2008-11-10
As a test only you might try running kompozer from the terminal using sudo. I'm at work right now and can't test this or I would. If that works, it would seem to indicate POSSIBLY a permissions issue. If that is the case, you may be able to find the offending folder and change the permissions to fix this.

I'll check it out later this week and see if it works.

---

