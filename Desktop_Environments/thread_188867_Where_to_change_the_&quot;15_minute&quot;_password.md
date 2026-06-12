---
title: "Where to change the &quot;15 minute&quot; password?"
date: 2006-06-04
forum: Desktop Environments
---

### Post by lzap on 2006-06-04
Hello,

I found out the sudo command remembers the password for 15 minutes. Can I change this value for example to 1 hour?

---

### Post by frenkel on 2006-06-04
If you have question like this, always consult the man-pages. Run this on the command line:
> man sudo

In there you will find this:
> ...once a user
       has been authenticated, a timestamp is updated and the user may then
       use sudo without a password for a short period of time (15 minutes
       unless overridden in sudoers)...

Have a look at the sudoers man page for an explanation how to change it.
> man sudoers

> 
...
 timestamp_timeout
                   Number of minutes that can elapse before sudo will ask for
                   a passwd again.  The default is 15.  Set this to 0 to
                   always prompt for a password.  If set to a value less than
                   0 the user&#8217;s timestamp will never expire.  This can be used
                   to allow users to create or delete their own timestamps via
                   sudo -v and sudo -k respectively.
....

You will need to edit the file /etc/sudoers (as root, so run something like sudo gedit /etc/sudoers) and add the following to the line that starts with Defaults:
> ,timestamp_timeout=60
So you get something like this:
> Defaults        !lecture,tty_tickets,!fqdn,timestamp_timeout=60

To keep the password remembered for 60 minutes.

---

### Post by lzap on 2006-06-05
Thank you very much. Is there any way to force unlearning (e.g. along with screensaver start).

---

### Post by frenkel on 2006-06-05
Didnt't you learn anything from what I posted? READ THE MAN PAGE!

> 
man sudo
...
       -k  The -k (kill) option to sudo invalidates the user&#8217;s timestamp by
           setting the time on it to the epoch.  The next time sudo is run a
           password will be required.  This option does not require a password
           and was added to allow a user to revoke sudo permissions from a
           .logout file.
...


sudo -k will forget the password.

---

### Post by lzap on 2006-06-05
Thanks.

---

