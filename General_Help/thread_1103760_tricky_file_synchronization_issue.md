---
title: "tricky file synchronization issue"
date: 2009-03-23
forum: General Help
---

### Post by MountainX on 2009-03-23
I need to synchronize files between my Ubuntu machine and a Windows computer. There are about 500,000 files (about 500 GB) on several different partitions. It is a big job.

The directory structures are not exactly the same, so that makes it tricky. I don't want to end up with duplicate files in two different directory trees. A normal synchronization would result in this.

Furthermore, one computer (my Ubuntu machine) has some newer files that need to be transferred over. It also has some older files that need to be deleted.

The rules I need to implement are:
1. any files on Ubuntu that have been modified (or created) within the last 30 days need to be copied to the Windows machine if they don't exist there (or are older there).
2. any other files that exist on Ubuntu and are not on the Windows machine need to be deleted from Ubuntu.
3. verify that there are no newer files on Windows than on Ubuntu -- I think this is the case, but maybe a few files have escaped my notice, so an verification is needed.
4. I probably need to manually match up the directories/folder because the tree structure is different.

Any idea how in the world to do this? Thanks.

---

### Post by hyper_ch on 2009-03-23
IMHO rsync can do it but no clue how it behaves with ntfs. I guess you'll have issues there.

---

