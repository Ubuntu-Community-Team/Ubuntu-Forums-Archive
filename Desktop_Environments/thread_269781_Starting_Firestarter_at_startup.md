---
title: "Starting Firestarter at startup"
date: 2006-10-02
forum: Desktop Environments
---

### Post by flummoxed on 2006-10-02
Hey,

I added the command 

```
gksu firestarter
```

to the startup programs in my sessions manager. This starts firestarter every time I log into ubuntu. The annoying thing about this is I have to enter my password twice every time I log in, the first time for the login screen and the second time because Firestarter requires a password to start. Is there any way I can store the password for Firestarter to start automatically?

---

### Post by wieman01 on 2006-10-02
> gksu firestarter
...starts the Firestarter GUI. So don't confuse that with Firestarter itself which is running by default (booted at startup). Pay attention to the boot process, it's also mentioned as one of the services there.

---

### Post by sefs on 2006-10-02
You make some modifications to your sudoers list.

I cant remember them off hand as I am not at my computer but seach the forum for these keywords....

sudo visudo

XAUTHORITY

XAUTHORIZATION


and you may find the mods you have to make to this file so as to not have to enter the password when gui stars up.

also instead of gksu firestarter you can use gksu firestarter --start-hidden to make the gui start minimized.

This is what my sudoers file looks like...
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

#Defaults       !lecture,tty_tickets,!fqdn
Defaults !lecture,tty_tickets,!fqdn,env_reset,env_keep+= " DISPLAY HOME XAUTHORIZATION "
# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

# User - Program Specific  privilege specification
yourusername        ALL= NOPASSWD: /usr/sbin/firestarter   

```

---

### Post by distroman on 2006-10-02
Notice that you need to use /sbin
[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)
Might want to use gksudo.

---

