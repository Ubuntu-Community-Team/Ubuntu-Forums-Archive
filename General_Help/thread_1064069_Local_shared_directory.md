---
title: "Local shared directory"
date: 2009-02-08
forum: General Help
---

### Post by wiz561 on 2009-02-08
Hi,

One of the many things I've been attempting to do is setup a local directory that is shared across all the users of my system.  I've attempted to do this with different chmod permissions and with the 'acl' package, but nothing works.  First off, this is a JFS file system.  When I tried to use acl in the fstab, it gave an error in dmesg.  I'm assuming JFS doesn't support this package.

Here's what I've tried...  Created a directory, such as "/data/test", change it to the group "users" (where all users of the system belong to), and set the permissions chmod -R a+rwx and create a file 'test.txt' as username 'mike'.  When I log out and log back in as 'joe', I cannot write to the file because it only has the "-rw-r--r--" permission and the owner is 'mike'.

I have to believe that there is a way to do this without screwing everything up.  This is one of the things that have been bugging me with unix and I know that there must be an answer out there.

Thanks in advance!
Mike

---

### Post by wiz561 on 2009-02-08
I know a LOT of people have this problem.  I finally figured it out...

Turns out that you don't have to put acl in fstab for xfs.  Just use setfacl and away you go.  here's what I did for others that are interested...

mkdir test
setfacl -d --set u::rwx,g::rwx,o::r-x test
chgrp users test
chmod -R g+w test
chmod -R g+s test

I think that seemed to do the trick.  We'll see what happens!

---

