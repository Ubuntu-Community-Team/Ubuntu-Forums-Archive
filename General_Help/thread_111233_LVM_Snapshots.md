---
title: "LVM Snapshots"
date: 2006-01-01
forum: General Help
---

### Post by j-a-p on 2006-01-01
I have been experimenting with LVM Snapshots and would like to get some input from others.

I've been looking for a way to backup my ideal Ubuntu setup.  I partitioned during installation using LVM so as I would easily be able to adjust my partitions later on.  I have my partitions how I want them and now want to backup everything.

So my idea was to create snapshots and then back them up.  All well and good, I have my backups.

As I have backed up my perfect system I now want to restore it to the exact state it was in when the backups were taken.  This is where I meet a problem.

It's all very well the backups I have taken are consistent, but when I restore, any files created after the backups were made remain after restoration.  I don't want this to happen.  I want to delete the newly created files.  Does anyone know how I can accomplish this?

I'm using tar to backup the snapshots and to restore.  I considered using dd, but I thought it was unnecessary to backup the unused space in the partitions.

Also I've read that snapshots can be used when testing software installation.  Apparently one can snapshot a volume mounted at /, and then mount the snapshot over the original volume, do the testing of new software and then remove the snapshot to revert backup to the original filesystem mounted at /.

I can't get this to work.  Anyone know?  I understand there must be some implications mounting a filesystem over one mounted at /.

I have looked elsewhere for answers to the problems, but no luck so far.  It doesn't seem that there are that many people using LVM in this way.  I think it looks really powerful if you can get your head round it.

All help appreciated.

---

### Post by psusi on 2006-01-01
When you restore from a tar backup, you usually do it to an empty ( cleanly formatted ) volume.  Tar doesn't delete things for you, it only extracts the files contained in the archive.

---

### Post by j-a-p on 2006-01-01
Appreciated, but what dou you suggest?

---

### Post by psusi on 2006-01-02
[QUOTE=j-a-p]Appreciated, but what dou you suggest?[/QUOTE]

I thought I was clear?  Format the partition before you restore.  Why are you restoring anyhow when the original data has not been lost?

By the way, you might want to take a look at daily backups with rsync.  Google for "rsync snapshot".

---

### Post by j-a-p on 2006-01-02
Yeah I get you.  Sorry for the misunderstanding.  It's all sweet now.

The reason I am restoring is just to test that in the event of a problem I will know that restoration will be good.

Thanks.

---

### Post by psusi on 2006-01-02
Oh, then you should restore to an empty directory or better yet, an empty disk, then make sure it all looks good.

---

