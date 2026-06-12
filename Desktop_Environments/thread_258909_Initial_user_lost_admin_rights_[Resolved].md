---
title: "Initial user lost admin rights [Resolved]"
date: 2006-09-16
forum: Desktop Environments
---

### Post by Chris Baldwin on 2006-09-16
My initial user id seems to have lost all the sys admin rights and is now just a basic user.  It worked OK when I first installed but sometime later after a restart everything had changed.

When I run gksu users-admin at the command line I get prompted for a password and then the message:

"Failed to run users-admin

The underlying authorisation mechanism (sudo) does not allow you to run this program. Contact the system administrator."

Help, without access to the root user I'm unable to make any system changes, install packages or set-up additional user accounts.

Thanks

Chris

---

### Post by RoyArne on 2006-09-16
Deleted because I was plain wrong.

---

### Post by ayoli on 2006-09-16
this page: 
[http://psychocats.net/ubuntu/sudo](http://psychocats.net/ubuntu/sudo)
might help you

---

### Post by ayoli on 2006-09-16
> **RoyArne said:**
> The root user is disabled on Ubuntu, by default. To run administrative apps try **gksudo users-admin** instead.

gksu is an gksudo alternative.
```
[22:06:31@ayoli.zone]:~ >$ ll /usr/bin/gksudo
lrwxrwxrwx 1 root root 4 2006-06-06 10:31 /usr/bin/gksudo -> gksu
```

---

### Post by Chris Baldwin on 2006-09-16
Thanks ayoli link you provided gave the answer.  Booted up in recovery mode and used command "addgroup <userid> admin" to put myself back in the admin group.  Back to normal now.

Thanks very much.

Chris

---

### Post by statelyplump on 2007-03-31
Thanks gang, I had the same problem occur after adding another group to my Initial User - I lost the admin rights (at least in Gnome, could not log in and view full admin menus).  Going to restore and following Chris' direction did the trick.  Thx.

---

### Post by jrev on 2007-12-24
I am on ubuntu feisty 7.04 and I suppressed the admin rights of the first user 

When I reboot in recovery mode to give him back the rights I get the message :
give root password for maintenance 

and when I give the first user password I get :
login incorrect

How did you do **then** to get the rights back ?

---

