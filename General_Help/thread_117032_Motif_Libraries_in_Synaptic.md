---
title: "Motif Libraries in Synaptic"
date: 2006-01-14
forum: General Help
---

### Post by Dean Powell on 2006-01-14
Hi:

I need to install Citrix ICA client in order to connect to work.  The latest version available from the website is 9, and it tells me I need OpenMotif 2.2.x to run successfully.  My archives are pointing to [http://archive.ubuntu.com](http://archive.ubuntu.com), but a search of libmotif yields nothing.  Nor can I find any reference to Open Motif in Synaptic.

I have downloaded the OpenMotif 2.2.3 source from the MotifZone website, but the compile fails, so going from source is not an option.

Can anyone tell me if there's an Ubuntu version of OpenMotif, or something that will support connecting through Citrix?

Thanks in advance!

Regards,
Dean Powell

---

### Post by cjazz on 2006-01-14
Lesstif is included in the Breezy repositories. That's the Hungry Programmers' implementation of OSF/Motif. Unfortunately, the latest version for Breezy is 2.1. I can't speak for Dapper.

Have you tried tsclient, which is in the repositories? I don't know if that would work for your purposes, but according to the description in Synaptic, it supports Citrix ICA client.

---

