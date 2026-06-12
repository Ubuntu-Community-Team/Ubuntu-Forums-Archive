---
title: "reiserfs and power outage"
date: 2009-02-03
forum: General Help
---

### Post by estyles on 2009-02-03
Hey, does anyone know if reiserfs is supposed to be, like, incredibly fragile?  We had a power outage last night (not even a storm, Com Ed just sucks, I guess), and my computer went down.  It is on a surge protector, although not a particularly great one.

Anyway, when I booted up, my /var partition and my /tmp partition, both of which are ReiserFS, were more or less fried.  Fsck could not fix them, and I was dumped to terminal on boot-up because the auto-disk check didn't work and told to fix the file system myself.  Of course, I don't know how to do that.  I tried to delete the partition and then recreate it, but it still couldn't pass disk check, and I couldn't get networking or anything else to work because the OS couldn't access /var or /tmp.  

Eventually, I figured out I could fix the problem by just commenting out the two lines in my fstab for /var and /tmp, and then "chmod a+rw /tmp", because for some reason the /tmp folder was read-only after the partition was unmounted.  Took me several hours to fix it.  (Obviously, woulda been faster if I knew how to do it in the first place.)

Anyway, long story short... I still want my /var and /tmp drives to be on separate partitions, but if ReiserFS is unstable, then I'll obviously use something else.  It just seems odd to me that my ext3 and ext2 partitions were fine, but both Reiser partitions were fried.  Of course, /var and /tmp are probably the only directories that were being written to at 3am this morning, since I didn't really have any processes running, so maybe that's it...

---

### Post by tgalati4 on 2009-02-03
Ups

---

### Post by estyles on 2009-02-03
> **tgalati4 said:**
> Ups

Thanks for the one word answer, but that's not what I'm asking.  I know a UPS can protect a computer.  And probably costs half as much as my entire machine.  =p  Unless you're telling me to have UPS *deliver* me a new computer?

I'm just asking, is Reiser really this fragile?  Journaling file-systems are supposed to not puke all over themselves everytime a write gets interrupted.  That's like literally the whole point of journaling.  Now, maybe I just got unlucky, and that's my question.  Am I unlucky, or have people heard/experienced similar problems with ReiserFS?  I've read that it's a good choice for /var because it handles small files and frequent writes really well, and without excessive fragmentation.  But if it can't recover from write interruptions, then that makes it a rough choice for anything that takes frequents writes.  And this wasn't just "oops, I lost some data", it was, "OMG my system is borked, what do I do?"  The fix turned out to be relatively trivial, but the symptoms of the problem were anything but.

---

### Post by tgalati4 on 2009-03-03
There are some stories of ReiserFS taking a dump.  A google search will turn up some interesting stories, including the developer's legal problems.

In theory it's faster; in practice it's less reliable. Try running a server for several years of uptime then let us know.  Ext3 and an UPS is  a good combo.  It's worked for me for 4 years straight on a server.

I've had to rebuild a Reiserfs once during that time.

---

