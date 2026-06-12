---
title: "Creating user directories with customized permissions using likewise-open"
date: 2009-06-01
forum: General Help
---

### Post by evank on 2009-06-01
A coworker of mine has connected an Ubuntu 9.04 box to our Active Directory domain with likewise-open5, and it went off without a hitch.  It's even set up to where, when a user logs into said Ubuntu box, a home directory is automatically created for them under **/home/DOMAINNAME/username** to which they have full ownership permissions.

However, we want to change the default permissions of these automatically created directories to also be read/write/execute by group (0775).  After much googling and traversing many mailing lists, we've made the following changes to the following files:

**_/etc/samba/smb.conf_**
```
[homes]
# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
    create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
    directory mask = 0775
```

**_/etc/samba/lwiauthd.conf_**
```
[global]
    directory mask = 0775
    create mask = 0775
```

**_/etc/likewise-open5/lsassd.conf_**
```
[auth provider:lsa-activedirectory-provider]
    # Umask for home directories
    # Default: 022
    #
    homedir-umask = 002
```

**_/etc/security/pam_lwidentity.conf_**
```
[global]
# the file-creation-mask for the home directory (default is 0022)
umask = 0002

```

Even with these changes in place, and after deleting a user directory, rebooting and logging in as the AD user again, the following is created:

```
$ ls -al /home/DOMAINNAME/ekaufman/
total 24
drwxr-xr-x 2 ekaufman domain^users 4096 2009-06-01 11:42 .
drwxr-xr-x 4 root     root         4096 2009-06-01 11:42 ..
-rwxrwxr-x 1 ekaufman domain^users  220 2009-06-01 11:42 .bash_logout
-rwxrwxr-x 1 ekaufman domain^users 3115 2009-06-01 11:42 .bashrc
-rw-r--r-- 1 ekaufman domain^users   48 2009-06-01 11:42 .k5login
-rwxrwxr-x 1 ekaufman domain^users  674 2009-06-01 11:42 .profile

```

As is evident, everything *within* the user's directory (**.bashrc**, **.profile**, and so on) is 0775, but the *directory itself* is still 0755.  What in the world are we missing?

---

