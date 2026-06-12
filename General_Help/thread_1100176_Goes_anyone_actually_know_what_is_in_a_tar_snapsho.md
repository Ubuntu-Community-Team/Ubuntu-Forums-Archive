---
title: "Goes anyone actually know what is in a tar snapshot file?"
date: 2009-03-18
forum: General Help
---

### Post by sofasurfer on 2009-03-18
I am trying to understand them.
I am able to create --listed-incremental archives but I feel incomplete not understanding what the snapshots contain and what they do.

When I create my level 0 archive, the /snar file sometimes has a number such as "37362826398" at the top and the a huge list of directories. Sometimes the number at the top is ALL that is in the file (if its a small directory being backed up).

Now, when I create a level 1 archive I use the same snapshot file that was created by the level 0 archive, as far as I have learned.

But when I create a level 3 (a second level 2) I have to copy snar to snar-1.

If the snapshot file is just used to determine which files have already been backed up, and thus, which files need to be backed up next, how come if you do a archive every day you need to keep all the snapshots. It seems to me that the snapshot for the level 0 and the most recent are the only ones that are required to keep.

Is there a logical way to understand snapshots?
Please don't recommend the Gnu Tar Manual. It does not explain beyond level 1(the second snar file).

---

### Post by sofasurfer on 2009-03-19
bump

---

### Post by geraldm on 2009-03-20
In a project snapshot, most projects will have the entire project files in the snapshot, as the repository was at one specific moment.  The snapshot would 
possibly differ from a release, in that the release would be checked to be sure that all the files are coordinated within the repository, and are generally expected to compile, and hopefully run as expected.  No such coordination is done with the snapshot, and on occasion, the snapshot might have unexpected errors in the run or in the compiling.  Unless expressly stated, do not expect a snapshot to be an incremental backup of files that have changed from a release.

regards,
Gerald

---

