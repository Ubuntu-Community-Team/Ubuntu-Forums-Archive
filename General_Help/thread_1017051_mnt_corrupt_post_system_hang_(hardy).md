---
title: "mnt corrupt post system hang (hardy)"
date: 2008-12-20
forum: General Help
---

### Post by dotdot on 2008-12-20
good evening all,
i run a variety of ubu variations (typing from an eee).
my jvc running hardy hung the other night on shutdown.
I have not been able to bring it up since..... it cant find my home.

my home is on a sep partition.

i bought it up into # prompt

ran fsck on everything - all came back with errs etc - ok fine.
reboot - still no joy.

brougt back into # then went into /etc/init.d

ran mount script to see if it would mount the fs it failed.

checked fstab - looks ok.
checked mtab .... ahem...
all ???? marks then a filename.

this file has an inode - but i alas don't seem to have clri to clear it.
(i've used that before thought diff os.)

anyone else seen this ?  - i think without a removal of this 
file i can't recreate it.... and thus i'm in limbo.

thoughts ideas - apprec.

cheers

..

---

### Post by SPr on 2008-12-21
> **dotdot said:**
> ran fsck on everything - all came back with errs

How many errors? What kind of errors? Sounds like the partition has been damaged to me.

---

