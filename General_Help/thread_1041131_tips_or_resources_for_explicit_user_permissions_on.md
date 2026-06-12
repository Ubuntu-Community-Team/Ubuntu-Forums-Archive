---
title: "tips or resources for explicit user permissions on linux files?"
date: 2009-01-16
forum: General Help
---

### Post by lumix on 2009-01-16
Can anyone point me toward a resource, concept or nomenclature to understand how user Fbar can be granted permissions for a file that neither he nor any of his member-groups own?  In other words, explicit, per-user permissions?

---

### Post by sisco311 on 2009-01-16
[https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by lswb on 2009-01-16
If I understand your question correctly, I don't believe it can be done using only normal unix/linux filesystem style permissions. These permissions are based on user, group, and "other" or everyone else. read/write/execute access can be specified for each of these categories. So using only file permissions, there really is no such thing as a "per-user" setting that would enable only selected non-owner, non-group-member users to access a file.

linux has an "acl" (Acess Control List) family of commands that can probably do what you want. Check "man acl" I don't have any experience with using the acl system myself but hopefully this info can get you started.

---

### Post by lumix on 2009-01-16
> **lswb said:**
> If I understand your question correctly, I don't believe it can be done using only normal unix/linux filesystem style permissions.


Hmm...so what is the conventional way (if there is one) to allow Joe User read access to file Foo, when Joe is not a member of the group that owns Foo?  I mean, it's quite common for, say, Joe in Human Resources to have a legitimate need for read access to, say, Accounting's Foo file, but not other files owned by Accounting.  How do I give Joe--but no one else in accounting--access to the Foo--but no other--file belonging to Accounting?

I've seen some information about ACL's, but it led me to believe that ACL's are *not* really "conventional", and in fact considered to be a "work in progress."

Surely folks *must* have been dealing with this need for many years now.

---

### Post by mssever on 2009-01-16
> **lumix said:**
> Hmm...so what is the conventional way (if there is one) to allow Joe User read access to file Foo, when Joe is not a member of the group that owns Foo?  I mean, it's quite common for, say, Joe in Human Resources to have a legitimate need for read access to, say, Accounting's Foo file, but not other files owned by Accounting.  How do I give Joe--but no one else in accounting--access to the Foo--but no other--file belonging to Accounting?

I've seen some information about ACL's, but it led me to believe that ACL's are *not* really "conventional", and in fact considered to be a "work in progress."

Surely folks *must* have been dealing with this need for many years now.
I think the conventional way to handle this is to create a special group for this purpose, add the relevant file(s) to that group, and add the relevant accounts to the group. This is actually a use case for which the standard Unix permissions model is poorly-suited. If you don't like the groups approach I outlined earlier, then ACLs are probably the best way to go.

Oh, there is another option, but I wouldn't really recommend it since it could quickly become confusing to manage: You could use hard links (ln -h) to the relevant files. Each hard link can have its own permissions, but point to the same file.

---

### Post by lumix on 2009-01-21
So *files* can be members of a group?  But even if so, if it were a member of more than one group, how do I specify the permissions that each group has on that file?

---

### Post by heindsight on 2009-01-21
> **mssever said:**
> You could use hard links (ln -h) to the relevant files. Each hard link can have its own permissions, but point to the same file.

This wouldn't work. permissions and ownership are stored in the inode, so all hardlinks to a file always have the same ownership and permissions.

---

### Post by mssever on 2009-01-21
> **lumix said:**
> So *files* can be members of a group?  But even if so, if it were a member of more than one group, how do I specify the permissions that each group has on that file?
Files aren't members of any group. Each file is owned by exactly one group. Users can be members of multiple groups. If a user is a member of the group that owns a particular file, that user has the permissions specified for the group for that file.
> **heindsight said:**
> This wouldn't work. permissions and ownership are stored in the inode, so all hardlinks to a file always have the same ownership and permissions.
OK. That makes sense. I stand corrected.

---

