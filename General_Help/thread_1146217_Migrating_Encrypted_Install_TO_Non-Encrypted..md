---
title: "Migrating Encrypted Install TO Non-Encrypted."
date: 2009-05-02
forum: General Help
---

### Post by ashton88 on 2009-05-02
Under Hardy I used the Ubuntu Alternative installation CD to install an encrypted install of ubuntu.  It has worked flawlessly since I did it.  The system is currently running Intrepid.  Recently I have become more paranoid with redundancy than security.

**How do you migrate off of an encrypted partition by rsync/mirroring to a unencrypted partition and then boot from that mirrored partition?**

(Or, am I going about this all the wrong way?  Is there a much easier way to do this?)

I have done this previously using rsync with *unencrypted* partitions as source and destination.  However, when I do the same thing from an encrypted partition to an unencrypted partition, when attempting to boot the unencrypted/mirrored partition, I still get prompted for the passphrase.

I don't know enough about what process/event/service calls that prompt and then mounts the encrypted drive.  I suspect that if I could "comment out" that event that the load would continue on the unencrypted drive just fine - but then again it may be more complex then that.

Inevitably, once I have this working and verify it, I will move off of the encrypted drive, and then delete the encrypted drive.  Encryption has worked flawlessly for me, but I have more concern for data loss and performance than data security at this point.

Looking for any input, from a solid answer to brainstorming from people that know more about Luks and encryption than I do (and I know nothing).

Many thanks!

---

