---
title: "Firestarter broken after upgrade"
date: 2006-07-04
forum: Desktop Environments
---

### Post by drpaul on 2006-07-04
After upgrading from Breezy I get the following when trying to start Firestarter

paul@paulsbox:~$ sudo firestarter
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:22757): Gtk-WARNING **: cannot open display:

Didn't even ask for password.

Any ideas?

Paul:confused:

---

### Post by jmeadows111 on 2006-07-04
You will want to investigate the security implications, but try the following command:

xhost +

then run the app.

---

### Post by Anduu on 2006-07-04
Try gksudo firestarter...

---

### Post by drpaul on 2006-07-05
gksudo yields the same as sudo.

the xhost + allowed the Firestarter to go. So what's wrong with my setup. I get a funny feeling that I may have done something bad for security. I got the message that access control disabled.????

Thanks

Paul

---

### Post by Anduu on 2006-07-05
Did you per chance use a how to for getting firestarter to run at startup which involved editing your sudoers file?

If so the method has changed slightly for Dapper...do a search for it.

---

### Post by drpaul on 2006-07-05
I don't have firestarter running at startup. There is some problem with giving it access to Xwindows. Turning off access control allows it to start. man xhost says there should be a X*.hosts file, but I can't find one. I don't know how to create it. Didn't need it with Breezy, but something is different with Dapper.

Any hints?

Thanx,

Paul

---

### Post by bogoliubov on 2006-08-10
> **drpaul said:**
> I don't have firestarter running at startup. There is some problem with giving it access to Xwindows. Turning off access control allows it to start. man xhost says there should be a X*.hosts file, but I can't find one. I don't know how to create it. Didn't need it with Breezy, but something is different with Dapper.

Any hints?

Thanx,

Paul

I have the exact same problem. I guess you haven't found a solution yet?

---

### Post by mlind on 2006-08-10
Looks like DISPLAY variable isn't preserved when you execute sudo commands. Is your sudo version 1.6.8p12-1ubuntu6 and does your /etc/sudoers look like
```

# /etc/sudoers
#
# This file MUST be edited with the '**visudo**' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

If you execute *sudo -s*, does your environment contain DISPLAY variable?
```

sudo -s
export | grep DISPLAY

```

---

