---
title: "ROOT undefined"
date: 2005-10-20
forum: Desktop Environments
---

### Post by tmattoneill on 2005-10-20
Hi there.  When I installed my 5.10 ubuntu it asked me to set up a user, but never asked me for a root password.  Now when I try to su root, it rejects whatever password i enter.  If there a default password that I should be using (i.e. admin or passwd or something) or how to I set this?  Other linux distribs i've used have always prompted for an admin or root pwd when installing.

Matt

---

### Post by GrumpyBob on 2005-10-20
Search the forum for "root" or "sudo"
For most purposes, Ubuntu uses sudo.  You can set a root user password, but it is not required by the default Ubuntu installation.

Robert

---

### Post by karuptdata on 2005-10-20
If you are looking to set up root password to use for terminal purposes just enter sudo su and enter user password and thats all if you want to set up root password which is not recommended just do sudo passwd root from terminal and set your root password hopes this helps!

---

### Post by tmattoneill on 2005-10-20
Okay before I go try this (since I can't get online in ubuntu due to my config using wireless) I'll just be clear with what I'm trying to do.

I've mounted my data drive (d) and it's created a directory I call d_drive (/dev/hda2).  When I did this under the Disk Management tool, it worked fine but d_drive is owned by "root"  I can't copy or do anything except view those files (oddly, I can view the files in firefox, but I can't copy them or do anything else as it says I don't have read permissions).  So I tried to su root so that I could copy the fles I needed to my home directory.  It asked for a password, which I never set up. I tried just hitting enter but it said "sorry".  Shouldn't I have a root password set up? Seems kinda dangerous not to have a password for root.

M

---

