---
title: "How do I sudo?"
date: 2005-05-13
forum: Desktop Environments
---

### Post by wwwolf on 2005-05-13
How do I sudo in one step? where I run sudo, application, and password in one step without being prompted for the password.

I want to be able to run sudo commands in a script or run sudo applications and assign then to the menu.

I'm sure its probably something like: 'sudo application::Password' but this doesn't work but shows how I would like to run sudo.

Any help would be appreciated.

Thanx,

---

### Post by Burgundavia on 2005-05-13
To run an application in the terminal, run 'sudo application'. To run them from Applications-->Run Application, run 'gksudo application'

Is that was you needed?

Corey

---

### Post by ludi on 2005-05-13
[QUOTE=wwwolf]How do I sudo in one step? where I run sudo, application, and password in one step without being prompted for the password.

I want to be able to run sudo commands in a script or run sudo applications and assign then to the menu.

I'm sure its probably something like: 'sudo application::Password' but this doesn't work but shows how I would like to run sudo.

Any help would be appreciated.

Thanx,[/QUOTE]
 Gnome
gksudo app or /path/to/app
Kde
kdesu app or /path/to/app

Terminal
$sudo app /path/to/app

There is a way to run sudo without any prompt the admin password (sudoers config, I think) but this isn't recommended.

---

### Post by bored2k on 2005-05-13
[http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)
That should explain better than us.

---

### Post by ludi on 2005-05-13
Well, I forgot to put the sudoers stuff, so here they are.
Some examples:

#username          ALL = (DB) NOPASSWD: ALL
#ALL            CDROM = NOPASSWD: /sbin/umount /CDROM,\
                /sbin/mount -o nosuid\,nodev /dev/cd0a /CDROM
#WEBMASTERS     www = (www) ALL, (root) /usr/bin/su www

Read the full document on:
[http://www.gsp.com/cgi-bin/man.cgi?section=5&topic=sudoers](http://www.gsp.com/cgi-bin/man.cgi?section=5&topic=sudoers)

I really, really don't recommend you do that. Some scripts can be load during the boot process without any prompts, whatever...

---

### Post by wwwolf on 2005-05-14
OK, thanx guys. 'kdesu application' works fine. I read that wiki page once but somehow I missed the kdesu part.  #-o

---

### Post by wwwolf on 2005-05-14
[QUOTE=ludi]Well, I forgot to put the sudoers stuff, so here they are.
Some examples:

#username          ALL = (DB) NOPASSWD: ALL
#ALL            CDROM = NOPASSWD: /sbin/umount /CDROM,\
                /sbin/mount -o nosuid\,nodev /dev/cd0a /CDROM
#WEBMASTERS     www = (www) ALL, (root) /usr/bin/su www

Read the full document on:
[http://www.gsp.com/cgi-bin/man.cgi?section=5&topic=sudoers](http://www.gsp.com/cgi-bin/man.cgi?section=5&topic=sudoers)

I really, really don't recommend you do that. Some scripts can be load during the boot process without any prompts, whatever...[/QUOTE]

Boy! This is confusing.  :-k 
OK lets say I want to just run a single application as root. (audacity) with no password. Would I do this?

sudo visudo /etc/sudoers

and add the line:

ALL              ALL = NOPASSWD: /usr/bin/audacity

Or have I totally missed the boat? 
 :-?

---

### Post by bored2k on 2005-05-14
```
export EDITOR=gedit && sudo visudo
```
> 
    # sudoers file.
    #
    # This file MUST be edited with the 'visudo' command as root.
    #
    # See the man page for details on how to write a sudoers file.
    #

    # Host alias specification

    # User alias specification

    # Cmnd alias specification

    # Defaults

    Defaults    !lecture,tty_tickets

    # User privilege specification
    root    ALL=(ALL) ALL

    # Added by Ubuntu installer
    reb    ALL=(ALL) ALL

    # Added by me to reboot/shut down without being asked password
    reb ALL = NOPASSWD: /usr/sbin/xfsm-shutdown-helper
That's an example.

---

### Post by ludi on 2005-05-14
You have to edit the sudoers file, just like this example ^^^ from bored2k .

---

