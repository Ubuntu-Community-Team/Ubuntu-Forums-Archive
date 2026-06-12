---
title: "Repost of trying to recuse root user-please help!"
date: 2006-01-20
forum: Desktop Environments
---

### Post by ubuntunewb75 on 2006-01-20
Ok as per last post i tried this to rescue my root account:

edit /etc/passwd and add root:x:0:0:root:/root:/bin/bash at the top (may require a live cd).  Reboot into single mode and type passwd.

I have done this.  Now I can sudo again (sort of!).  after sudo su'ing and typing passwd, I received this error message:

passwd: Authenticaton service cannot retreive authentication info.

I can get to root through sudo but  I cannot apt either.  It all seems hinged on this authentication issue.  Please please help with any idea!

---

### Post by az on 2006-01-20
[QUOTE=ubuntunewb75]Ok as per last post i tried this to rescue my root account:

edit /etc/passwd and add root:x:0:0:root:/root:/bin/bash at the top (may require a live cd).  Reboot into single mode and type passwd.

I have done this.  Now I can sudo again (sort of!).  after sudo su'ing and typing passwd, I received this error message:

passwd: Authenticaton service cannot retreive authentication info.

I can get to root through sudo but  I cannot apt either.  It all seems hinged on this authentication issue.  Please please help with any idea![/QUOTE]

what is the contents of your /etc/sudoers file?

You should be able to fix it by booting into recovery mode.

---

### Post by ubuntunewb75 on 2006-01-20
Here is my sudoers file.

I am currently in recovery mode as we speak.  It did ask for root password for maintenance but there isnt one so i pushed ctrl-C to skip.  should I do an adduser root?  or does that not accomplish what I need?


# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

---

