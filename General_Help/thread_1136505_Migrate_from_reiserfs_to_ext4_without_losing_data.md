---
title: "Migrate from reiserfs to ext4 without losing data?"
date: 2009-04-25
forum: General Help
---

### Post by infinitejones on 2009-04-25
The question's as simple as that - is it possible?

My /home partition is reiserfs (don't ask why, I set it to that when I first install Ubuntu about three years ago and I've never changed it) but it sounds like it would make sense now to to migrate it to ext4.

I know it's relatively trivial to back it all up and re-format it, but is there a way to do it without re-formatting?

Or - does it actually not make much difference anyway?

---

### Post by kidders on 2009-04-26
Hi there,

> **infinitejones said:**
> it sounds like it would make sense now to to migrate it to ext4.Not necessarily. For example, if your box is in any way unstable (ie you play around with it a lot, and it crashes every now and then), switching to ext4 could result in more data loss than you're accustomed to with reiserfs or ext3.

> **infinitejones said:**
> is there a way to do it without re-formatting?No. The two filesystems have absolutely nothing in common, so there is no way to transform one into the other on the fly.

If you have an external hard disk (or another computer on your network), you could do it this way ...[LIST]
[*]Shut down X and become root. Use **lsof** to make sure no files in /home are open.
[*]If the target filesystem (and network protocol) supports unix style permissions run **cp -dpR /home /path_to_backup**. If not, you should tarball your /home filesystem first, and copy that instead. I would strongly suggest **md5sum**-ing the tarball after you copy it.
[*]Unmount & rewrite the filesystem with **mkfs**.
[*]Change your /etc/fstab and run **mount -a** to simulate rebooting.
[*]Check that your /home mounted and copy all your stuff back into it.
[*]Restart your graphical environment & log back in.
[/LIST]

I hope that helps.

---

### Post by infinitejones on 2009-04-26
Thanks very much - that's answered the question - I'll leave it as it is!

---

