---
title: "Sudo + admin-time"
date: 2006-08-31
forum: Desktop Environments
---

### Post by gen0c1de on 2006-08-31
I am currently looking in to a solution that will allow users that don't have admin rights to be able to change the time and date if necessary.  I have been looking in to using sudo for this task, however it isn't quite playing nicely.

Here is my sudoer:

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
test    ALL=(ALL) /usr/bin/time-admin


```

so the test user has access to run the time-admin command that should allow that user to change the time.  However that isn't the case, gnome asks for a password to gain access, but when the user inputs a correct password it doesn't present the time configureation window.

This is what i get in the auth.log file when test tries to login

test : TTY=unknown ; PWD=/ ; USER=root ; COMMAND=/usr/bin/time-admin

So i'm stuck, any insight would be helpful.  Thanks

---

### Post by gen0c1de on 2006-08-31
*Update*

if i replace the admin-time with a command line only command it works fine, it just isn't playing well with graphical programs well.  Any ideas?

---

