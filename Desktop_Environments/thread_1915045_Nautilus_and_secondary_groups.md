---
title: "Nautilus and secondary groups"
date: 2012-01-25
forum: Desktop Environments
---

### Post by magwart on 2012-01-25
OS: Ubuntu 10.04

I have a set of users that have their 'private' group as their primary group, but also belong to a set of secondary groups:

Username: jim   Groups:  jim (primary), foo
Username: bob   Groups:  bob (primary), foo

In order to facilitate sharing files between Jim and Bob, I created a directory called /shared with the group sticky bit:

ls -ld /shared
drwxrwsr-x 2 jim foo 4096 Jan 25 11:06 /shared

Now Jim can create, read, and write files in /shared with no problem (after all, he's the owner).  Bob can do the same, but only after he runs 'newgrp foo'.

The problem that I have is that Bob prefers to use Nautilus to move files around.  Nautilus runs with the effective group set to the user's primary group (in this case, egid='bob').  If Bob tries to create a new file or folder in /shared, Nautilus refuses (the 'create folder' menu entry is greyed out) because Bob doesn't have permission.

I tried using setfacl to set more fine-grained permissions on /shared, but /shared is actually a NFS mount, but acls do not work the same on NFS as they do on a NFS mount.  I also tried to start Nautilus with:

newgrp foo
nautilus -q

...but nautilus continues to run using Bob's primary group.

How can Bob use Nautilus to create new files in this shared directory?  Is there any way to start a nautilus instance that uses Bob's secondary group?

---

### Post by LewisTM on 2012-01-25
This behavior sounds suspicious. If a user is a member of a group that has write access, he/she should be able to create files. The primary group is irrelevant and Nautilus should work.

It might be a problem with the NFS setup, for instance the server forcing a single user and group on the share.

---

### Post by magwart on 2012-01-25
Thank you for the tip.  In fact, when I try this on a local directory, it works as expected.  It's only when I try to use group writable/sticky bits on NFS mounts that it fails.  I'll poke around my NFS configuration a bit more and follow up here if I come across a solution.

---

### Post by magwart on 2012-01-26
This is finally solved.  I had to make two changes on the nfs server to support this:

Remove the --manage-gids flag from mountd in /etc/default/nfs-kernel-server

Ensure that all uids/gids in the nfs exports map to valid usernames on the nfs server (lots of /etc/passwd updates).  If this is not done, then the client when you try to mount the filesystem from the nfs server (it looks like it's related to this:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/409366](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/409366))

---

### Post by LewisTM on 2012-01-26
Glad you've found a solution.
I've made some tests with the stock NFS config in 11.10 and the problem is not there. 
A user with a non primary but write permitted group can create files on a SGID directory.

Cheers!

---

