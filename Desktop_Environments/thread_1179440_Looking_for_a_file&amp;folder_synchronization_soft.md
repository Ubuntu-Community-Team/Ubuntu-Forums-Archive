---
title: "Looking for a file&amp;folder synchronization software"
date: 2009-06-05
forum: Desktop Environments
---

### Post by xiamx on 2009-06-05
I'm looking for a file & folder synchronization software which supports Samba shares, local folders  with ignore list and cron job. Webdav support is also appreciated but it's not so important.Both CLI and GUI are fine, gtk is better.  I've tried Conduit. it works, but it doesn't support cron neither ignore list. Does anyone knows a good synchronization software?
Thanks

---

### Post by hictio on 2009-06-05
Have you tried rsync? It is installed on Ubuntu by default AFAIK, it is CLI, but there are many GUI (even webfronts) for it.

---

### Post by Tibuda on 2009-06-05
> **hictio said:**
> Have you tried rsync? It is installed on Ubuntu by default AFAIK, it is CLI, but there are many GUI (even webfronts) for it.

Yes, rsync is great. I use grsync as a frontend (it uses Gtk+, as you want).

---

### Post by xiamx on 2009-06-05
> **hictio said:**
> Have you tried rsync? It is installed on Ubuntu by default AFAIK, it is CLI, but there are many GUI (even webfronts) for it.
I'm trying rsync now, and i'll post back the result later

---

### Post by xiamx on 2009-06-05
Works great, CLI interface, so i'm able to right a bash script and turn it into a cron job
Ehm, how about two way synchronization? does rsync support two way synchronization ( it can be very useful to synchronize work between usb key and harddrive) ? if not does some else software support?

---

### Post by terrrorr on 2009-06-07
Hi,

Have you tried Unison. I used it couple years ago and it worked like a charm.

- Terrrorr

---

### Post by hictio on 2009-06-07
> **terrrorr said:**
> Hi,

Have you tried Unison. I used it couple years ago and it worked like a charm.

- Terrrorr

++
If you want two way sync.
[Unison](http://www.cis.upenn.edu/~bcpierce/unison/)

---

### Post by gg234 on 2009-06-08
try this guide

[http://www.ubuntugeek.com/unison-file-synchronization-tool.html](http://www.ubuntugeek.com/unison-file-synchronization-tool.html)

---

