---
title: "autentication error (no switch to root user)"
date: 2009-11-02
forum: Desktop Environments
---

### Post by alex69 on 2009-11-02
Hi,

I just upgrade to karmic and I'm experiencing this kind of problem:
needing administrative rights, I'm used to act in 2 ways:

1) with

```
su root
``` + root password 

but in this way my new karmic continue to repeat the same msg:Autentication error!!
just like if I fault the password entry, but I've tried very much time with all kind of check on it and I'm sure: the root password I wrote is absolutely correct! ??


2) using nautilus with the terminal command

```
sudo nautilus
``` + root password;

in this way nautilus works good as admin anyway, while nautilus it's launching, the following errors come out from terminal:

```
(nautilus:5824): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension
** Message: Initializing gksu extension...

** (nautilus:5824): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:5824): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:5824): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-open-terminal extension

** (nautilus:5824): WARNING **: Could not inhibit power management: The name org.gnome.SessionManager was not provided by any .service files

--- Hash table keys for warning below:
--> l2067
--> inode/directory
--> root

```

Is there anyone able to understand what's happening to my authentication system? why < su root > do not work properly with Karmic?

---

### Post by systemgod on 2009-11-05
I seem to have the same problem. 'su - root' gives

su - root
Password: 
su: Authentication failure


However 'ssh -l root localhost' with the same password works fine.  I'm using Kerberos/LDAP authentication which may be creating problems here.

Nico

---

### Post by systemgod on 2009-11-06
Solved by installing nscd (name service caching daemon).  nscd needs to be running for this to work.

---

