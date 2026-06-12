---
title: "Active Directory Home Directories, Automatic mapping of drives and Kerberos"
date: 2022-01-25
forum: Desktop Environments
---

### Post by alslinet on 2022-01-25
I have been struggling with this for a while, but cant seem to make sense of it.
I have the following requirements.

When a user with active directory / kerberos credentials logs in i want ubuntu to get their home directory from active directory and connect to it using kerberos.
The servername can be different depending on the user.

I found several solutions where the server name is predicatable, but in this case its not.

How would i go about doing this?

---

### Post by TheFu on 2022-01-25
Is the HOME directory local storage or remote storage?
Are there any snap packages installed which are being used as part of logins?
Where are the HOME directories mounted?
Is the storage all native Linux (ext3/4, f2fs, zfs, btrfs, or one of those)?  It cannot be samba/CIFS or NTFS or exFAT.
At login, what do the system logs show?

BTW, I've never used AD or Kerberos related to Linux logins, but I have used LDAP DBs for user and group credentials and autofs to mount a user's HOME.  If snaps are used, I think all of this is broke.  [https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1662552](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1662552) They've known about it for years.  I also know that if HOME directories aren't mounted to /home, snaps won't work.  So, of the login DE requires a snap package, the logins will fail.

---

