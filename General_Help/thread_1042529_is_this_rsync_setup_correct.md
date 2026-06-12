---
title: "is this rsync setup correct?"
date: 2009-01-17
forum: General Help
---

### Post by DiGiTY on 2009-01-17
I set up rsyncd (server) on my ubuntu home server primarily to sync from my iTunes music folder and to have my other files and folders sync up to it. This is where I'm confused... I want my music files to sync to the server, but not from the server (e.g., one way sync only, like mirroring) and I want any other profiles I set up to sync both ways.... I'm assuming I can only sync both ways with rsync... does this mean I have to set up a rsync server too on the Windows computer and set the music profile to read only?

---

### Post by mdurham on 2009-01-17
I think rsync only syncs one way.

---

### Post by albinootje on 2009-01-17
> **DiGiTY said:**
> I want my music files to sync to the server, but not from the server (e.g., one way sync only, like mirroring) and I want any other profiles I set up to sync both ways....

For rsync you only need ssh server installed on both machines.
Then you can use rsync in a script to do backups or "syncing" either way.

---

