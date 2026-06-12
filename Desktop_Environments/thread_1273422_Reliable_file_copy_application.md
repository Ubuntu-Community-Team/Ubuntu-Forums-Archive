---
title: "Reliable file copy application"
date: 2009-09-23
forum: Desktop Environments
---

### Post by DrObviousSo on 2009-09-23
I have a laptop on a less than reliable wifi connection and a local network attached storage server.  I'm looking for a reliable file copy application that will detect when a file copy to/from the nas has failed and retry it.

When I'm using my windows machine, terracopy does this really well, but I haven't been able to find an application or setting in nautilus for this in ubuntu.  Any suggestions?

---

### Post by sedawk on 2009-09-23
You can use rsync to copy stuff and then run it again
to see everything is in sync.

I guess you mount the NAS drive locally, so you run
rsync on two local directories.
But you can also use rsync over the network, e.g.
via rsync or ssh protocol.

---

### Post by DrObviousSo on 2009-09-23
Thanks for the reply.

You are correct, I mount the nas locally.  However, I really just need to grab one arbitrary file from the nas and copy it somewhere arbitrary on the local disk.  

My ideal use case would be more like "I need some giant media file from the nas -> browse to the giant file w/ nautilus or some other gui -> copy -> browse to desktop or temp folder on local disk -> paste"

From what I've read of rsync, an entire directory gets synchronized.  I wouldn't really want to have to sync an entire folder of giant files.

---

### Post by DrObviousSo on 2009-09-27
So it appears that rsync is by default one way syncing, not both ways, and any of the rsync GUI's work just fine for me.

---

