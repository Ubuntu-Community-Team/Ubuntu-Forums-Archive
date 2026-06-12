---
title: "can someone please post their &quot;/etc/sudoers&quot;"
date: 2006-03-20
forum: Desktop Environments
---

### Post by %hMa@?b&lt;C on 2006-03-20
I switched to mepis because of my video card being easier to set up on my dad's computer, and sudo doesnt work. please post your sudoers file for me.
it is located at /etc/sudoers
thanks!

---

### Post by eriefisher on 2006-03-20
I beleive Mepis uses "su". Type "su" and then password for root access. I think this is what you want.

eriefisher

---

### Post by Absolute on 2006-03-21
If it helps!

```
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
jeff    ALL=(ALL) ALL

```

---

### Post by lorap on 2006-03-21
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

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin	ALL=(ALL) ALL

---

