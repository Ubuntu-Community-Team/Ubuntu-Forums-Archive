---
title: "allow normal user shutdown and restart without password"
date: 2011-01-28
forum: Desktop Environments
---

### Post by cccc on 2011-01-28
hi

I have Ubuntu 10.10.
Howto allow normal user shutdown and restart without password?

---

### Post by cccc on 2011-01-28
I added these lines in /etc/sudoers:```

# cat /etc/sudoers
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification
**User_Alias USERS = ubuntuuser**

# Cmnd alias specification
**Cmnd_Alias SHUTDOWN_CMDS = /sbin/shutdown, /sbin/reboot, /sbin/halt**

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
**USERS ALL=(ALL) NOPASSWD: SHUTDOWN_CMDS**

```
but this problem still exists.

---

### Post by Copper Bezel on 2011-01-29
What's your specific goal here? I mean, obviously, you can do these things without a password through the GUI, so why do you need them in CLI?

---

### Post by cccc on 2011-01-29
> **Copper Bezel said:**
> What's your specific goal here? I mean, obviously, you can do these things without a password through the GUI, so why do you need them in CLI?

I've removed Gnome and have just CLI.

---

### Post by CharlesA on 2011-01-29
You'd still have to use sudo, it just won't prompt you for your password.

---

### Post by cccc on 2011-03-27
> **CharlesA said:**
> You'd still have to use sudo, it just won't prompt you for your password.

Thx, but just wondering if is it any way to do it without using sudo?

---

### Post by CharlesA on 2011-03-27
> **cccc said:**
> Thx, but just wondering if is it any way to do it without using sudo?
I don't think it's possible to do it without using "sudo"

Could create an alias, but that doesn't get rid of the problem.

---

