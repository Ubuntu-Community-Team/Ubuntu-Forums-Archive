---
title: "I think I hosed my sudoers file"
date: 2010-03-29
forum: Desktop Environments
---

### Post by Yadda on 2010-03-29
Hello,

I hosed the permissions on my sudoers file and attempted to fix it by deleting it. I then followed [This ]("http://ubuntuforums.org/showthread.php?t=737766") to get it back. When I replaced the sudoers file my default user no longer had root access so I added my user to the sudoers file. I now have sudo right again but weirdness remains. I created a file is /var/log/ using 
```
 sudo touch /var/log/file 
```

now when I try to delete that file with

```
 sudo rm /var/log/file 
``` I get a permission denied error. what am I doing wrong?

The following is my sudoers file:
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults env_reset
#Defaults env_reset, !set_logname

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root ALL=(ALL) ALL
<my_username> ALL=(ALL) ALL


# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
#%admin ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
#%admin ALL=(ALL) ALL 
```

Thanks!

---

### Post by adam814 on 2010-03-29
Why not just uncomment the relevant entry and add your user to the admin group?  While you *can* do it that way sudo usually works better with groups rather than usernames.

---

