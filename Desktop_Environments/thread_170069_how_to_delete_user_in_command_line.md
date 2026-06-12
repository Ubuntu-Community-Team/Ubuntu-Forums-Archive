---
title: "how to delete user in command line?"
date: 2006-05-03
forum: Desktop Environments
---

### Post by corteze on 2006-05-03
sudo userdel "username" doesn't seem to work.
any ideas?

---

### Post by aysiu on 2006-05-03
When you say "doesn't seem to work," what do you mean? Do you get errors? If so, what? If not, what makes you think it doesn't work? ```
USERDEL(8)                                                                                                            USERDEL(8)

NAME
       userdel - Delete a user account and related files

SYNOPSIS
       userdel [-r] login_name

DESCRIPTION
       The userdel command modifies the system account files, deleting all entries that refer to login_name. The named user must
       exist.

OPTIONS
       The options which apply to the userdel command are:

       -r     Files in the user’s home directory will be removed along with the home directory itself and the user’s mail spool.
              Files located in other file systems will have to be searched for and deleted manually.

FILES
       /etc/group
              group account information

       /etc/login.defs
              shadow password suite configuration

       /etc/passwd
              user account information

       /etc/shadow
              secure user account information

EXIT VALUES
       The userdel command exits with the following values:

       0      success

       1      can’t update password file

       2      invalid command syntax

       6      specified user doesn’t exist

       8      user currently logged in

       10     can’t update group file

       12     can’t remove home directory

CAVEATS
       userdel will not allow you to remove an account if the user is currently logged in. You must kill any running processes
       which belong to an account that you are deleting. You may not remove any NIS attributes on a NIS client. This must be
       performed on the NIS server.

SEE ALSO
       chfn(1), chsh(1), passwd(1), login.defs(5), gpasswd(8), groupadd(8), groupdel(8), groupmod(8), useradd(8), usermod(8).

AUTHOR
       Julianne Frances Haugh (jockgrrl@ix.netcom.com)

                                                           09/30/2005                                                 USERDEL(8)
```

---

### Post by corteze on 2006-05-03
well, thats the thing, i'm not getting anything, 
i do that command and i log off and I can still login as deleted user.

---

### Post by aysiu on 2006-05-03
You're not trying to delete the user when you're logged in as the user you're trying to delete, are you?

---

### Post by corteze on 2006-05-03
no, i have setup new user and i'm trying to delete one that was setup during installation.

---

### Post by cgjones on 2006-05-03
If you want, try it again, then type the following and post the result here.
```

echo $?

```

---

### Post by corteze on 2006-05-03
it was a fresh installation so i guess it's much quicker to reinstall   
then google for 2 hours. thanks for help anyway.

---

### Post by Ingwar on 2006-05-17
**aysiu**, thanks a lot for the post. I could not login anymore being stuck at the splash window ](*,) and created new user. Then I could not delete the old non-working user's "home" files. Your post did help. =D>

---

### Post by Quads on 2008-02-16
I get the error back "Unable to lock password file"

---

