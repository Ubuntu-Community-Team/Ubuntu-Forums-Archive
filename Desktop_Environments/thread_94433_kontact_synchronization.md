---
title: "kontact synchronization"
date: 2005-11-24
forum: Desktop Environments
---

### Post by hatefulthreatening on 2005-11-24
I have kubuntu installed on my laptop and my desktop, and I use kontact and kdewallet on both of them.

How do I keep my mail/rss feeds/contact lists/passwords and so on in sync between the two machines?

I looked around apt and the stuff installed by default, but all I can find are programs that sync with palm pilots and such... Is there some feature integrated into kontact that I'm just missing?

---

### Post by ltmon on 2005-11-24
Kontact has a synchronisation part that syncs addresses and appointments.  I'm not sure if it will do emails/rss/wallet etc. unfortunately.

Is the sync program not in your contact "main" list (the very bottom entry).

If not try:
multisynk
multisync
kitchensynk

Be aware that synching is definately not KDE's strong point right now (a new solution "OpenSync" is in the works, but not available now).  One of those programs should be able to synchronise between two files.  If you make your laptop's resources available via ftp, nfs or similar you should be able to sync.

---

### Post by hatefulthreatening on 2005-11-25
That's unfortunate. Maybe I can roll something together with ssh and rsync. Sync the configuration files and mail folders and such..

---

