---
title: "Can I restore a deleted file on ubuntu 6.06 server?"
date: 2006-08-20
forum: Desktop Environments
---

### Post by narrowband on 2006-08-20
Is there a wastebasket on the server version of ubuntu and how do I get to it to restore a deleted file?

---

### Post by noof on 2006-08-20
It's gone if you did "rm", and it you're using ext3:
> Q: How can I recover (undelete) deleted files from my ext3 partition?
Actually, you can't! This is what one of the developers, Andreas Dilger, said about it:

In order to ensure that ext3 can safely resume an unlink after a crash, it actually zeros out the block pointers in the inode, whereas
ext2 just marks these blocks as unused in the block bitmaps and marks the inode as "deleted" and leaves the block pointers alone.

Your only hope is to "grep" for parts of your files that have been deleted and hope for the best.

---

