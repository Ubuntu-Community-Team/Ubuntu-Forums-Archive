---
title: "Lost root access"
date: 2006-08-08
forum: Desktop Environments
---

### Post by frostie on 2006-08-08
I seem to have lost the ability to run any sysadmin tasks and things such as user admin and login window are no longer listed in the system>admin menu, despite being checked in alacarte.
The last thing I did was to create a new user account for which I checked the box to 'allow system admin'. Since then I no longer have any sudo access to anything neither can I run such things as synaptic (from the command line)

$ sudo synaptic

gives me a message about the underlying mechanism not allowing this and to contact the system administrator. This is true in both the original and new accounts.

Running 

$sudo <a command>

drops me back at an empty prompt with nothing happening. (it will ask me for a password the first time but then drop me back at the prompt after that).

I'm not sure what I should do or what has happened. (I was actually hoping to create a new account for myself (with a different username of course)).

regards,

---

### Post by Ramses de Norre on 2006-08-08
What's the output of "groups"?

And if admin is listed, can you boot into recovery mode and check the contents of /etc/sudoers (with the cat or less command) and post it here too?

---

### Post by frostie on 2006-08-08
$ groups
robert adm dialout cdrom floppy audio dip video plugdev scanner share

$ cat /etc/sudoers

# Defaults
Defaults   !lecture,tty_tickets,!fqdn

#User privilege specification
root ALL=(ALL) ALL

#Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

(typed from recovery mode, there are a few usual commented out lines leading up to this)

regards,

---

### Post by taurus on 2006-08-08
Boot into a recovery mode (from GRUB menu) and add yourself back to group admin in /etc/group...

```

nano /etc/group

```

---

### Post by Ramses de Norre on 2006-08-08
You aren't in the admin group, which is the group defined in /etc/sudoers to get sudo priviliges.
To fix: adduser username admin (in recovery mode, substitute "username" by the actual value).

---

### Post by aysiu on 2006-08-08
Full recovery instructions:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by frostie on 2006-08-08
Perfect. Thank you for your help.

---

### Post by frostie on 2006-08-08
Sorry, bit quick with the post there...

Thanks Ramses de Norre for all your help, all is now well and I have root access on my new account.

Thank you also aysiu for the link, now bookmarked.

regards,

---

### Post by Ramses de Norre on 2006-08-08
You're welcome ;)

---

