---
title: "restrict access with rbash &quot;gone wrong&quot;"
date: 2009-05-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sirius1 on 2009-05-17
Ubuntu 8.04.1 Dell mini 9

Followed these directions: [http://blog.bodhizazen.net/linux/how-to-restrict-access-with-rbash/](http://blog.bodhizazen.net/linux/how-to-restrict-access-with-rbash/)

Now the restricted user can't even logon to their desktop.  Error message when they attempt to login: User's $HOME/dmrc file is being ignored. This prevents the default session and langueage from being saved. File should be owned by user and have 644 permission.User's $HOME directory must be owned by user and not writable by other users.

I checked "OK" then got error message: The Gnome session manager was unable to lock the file '/home/ruser/. 
iCE authority'. Please report this aas a GNOME bug. Sometimes this error may occur if the file's directory is unwritable, you could try logging in via the failsafe session and ensuring that it is. "OK"

Clicked "OK" arrived at my admin account prompting me for my password, entered and logged into my admin account to send this thread.

[CODE]
dharma@dharma:~$ cat/etc/sudoers
bash: cat/etc/sudoers: No such file or directory
dharma@dharma:~$ sudo cat /etc/sudoers
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
ALL	ALL=NOPASSWD: /sbin/initctl emit boot-phase ui-started -n

Please help me undo my mistake, very grateful for your valued time.

Larry

---

### Post by sirius1 on 2010-06-12
This looks a lot more hairy than it turned out to  be.

I basically made an account useless, by futzin with rbash
(rbash is a command used to restrict users -believe me it works...)

When I boot, I got this error message:

User's $HOME/dmrc file is being ignored. This prevents the default session and langueage from being saved. File should be owned by user and have 644 permission.User's $HOME directory must be owned by user and not writable by other users.

The settings for owner and or permissions got messed up in the initialization file.

Following these steps enabled me to login to the problem desktop.

$ sudo chown username:username /home/username/.dmrc
$ sudo chmod 644 /home/username/.dmrc
$ sudo chown username:username /home/username
$ sudo chmod 755 /home/username

I found the above dmrc commands at:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

Dell Mini 9
Also, I found it helpful to know a few key combinations to get around in this seemingly cryptic form of a terminal.

Up arrow (lets you scroll through previous commands saves typing using up/down arrow keys)

Shift + Fn + up arrow (to scroll up or down the screen)

These key combinations will be slightly different depending on your model.

---

