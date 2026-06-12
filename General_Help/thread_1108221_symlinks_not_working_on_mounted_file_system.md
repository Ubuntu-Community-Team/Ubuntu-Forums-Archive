---
title: "symlinks not working on mounted file system"
date: 2009-03-27
forum: General Help
---

### Post by MountainX on 2009-03-27
I logged in to my file server via SSH and I created a symlink (ln -s /target linkname). I tested it with "cd linkname" and it works. The purpose of the symlink is for NFS clients to use it via mounted file systems.

Then, on my local machine I opened Nautilus and browsed to the folder that holds the symlink. It show "link (broken)" and indeed the link does not work. But it still works in the terminal when I SSH to the file server.

What do I need to do so that symlinks will work as expected on the NFS mounted file system? (And the symlink should still work on the server locally.)

EDIT:
[This link]("http://ou800doc.caldera.com/en/SDK_sysprog/_Using_Symbolic_Links_with_NFS.html") explains the problem, but I still have not found a solution that will allow the same symlink to function correctly when used from the server and the client. It seems like I will need a set of symlinks for the clients to use and another set of symlinks for local use on the server; and one set will always appear to be broken... not good

---

