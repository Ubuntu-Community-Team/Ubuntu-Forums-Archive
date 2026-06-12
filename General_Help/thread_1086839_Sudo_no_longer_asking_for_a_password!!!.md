---
title: "Sudo no longer asking for a password!!!"
date: 2009-03-04
forum: General Help
---

### Post by Ms_Angel_D on 2009-03-04
Hi,

For some reason Sudo has stopped asking for my password and I can't figure out why, I haven't done anything purposely to change this behavior. I do know I'm not comfortable with it and I would like the old behavior back. Does anyone have any Ideas how I might fix this.

Thanks,
Angel

---

### Post by mirrorhall on 2009-03-04
Reboot!

Problem persists? (Problem!)

Otherwise this is a session issue. Gnome-Keyring keeps the authorisation for the current session.

Still a problem after a reboot? --> check the visudo file...

---

### Post by Ms_Angel_D on 2009-03-04
> **mirrorhall said:**
> Still a problem after a reboot? --> check the visudo file...

How would I go about doing this?

---

### Post by Jordanwb on 2009-03-04
If you use sudo several times within a few minutes it won't ask you. But if you wait a certain amount of time it'll require you to retype the password.

---

### Post by heindsight on 2009-03-04
> **MetalHellsAngel said:**
> How would I go about doing this?

Actually it's the sudoers file, located at /etc/sudoers.

The command to edit the file is visudo, run it like:
```
sudo visudo
```

If you just want to inspect the contents of the file, without changing it, do:
```
sudo cat /etc/sudoers
```

---

### Post by Ms_Angel_D on 2009-03-04
> **Jordanwb said:**
> If you use sudo several times within a few minutes it won't ask you. But if you wait a certain amount of time it'll require you to retype the password.

Thanks for your reply unfortunately I'm certain this isn't the case.

if this helps anyone this is from my auth.log file

```
Mar  4 09:55:48 angel-desktop sudo:    angel : TTY=unknown ; PWD=/home/angel ; USER=root ; COMMAND=/usr/bin/nautilus
Mar  4 09:56:02 angel-desktop sudo:    angel : TTY=unknown ; PWD=/home/angel ; USER=root ; COMMAND=/usr/bin/nvidia-settings
Mar  4 09:57:40 angel-desktop gdm[6111]: pam_unix(gdm:session): session closed for user angel
Mar  4 09:57:45 angel-desktop gdm[7282]: pam_nologin(gdm:auth): cannot determine username
Mar  4 09:57:49 angel-desktop gdm[7282]: pam_unix(gdm:session): session opened for user angel by (uid=0)
Mar  4 09:57:49 angel-desktop gdm[7282]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Mar  4 09:57:49 angel-desktop gdm[7282]: gnome-keyring-daemon: couldn't lookup keyring component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Mar  4 09:57:49 angel-desktop gdm[7282]: Autolaunch error: X11 initialization failed.
Mar  4 09:57:49 angel-desktop gdm[7282]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Mar  4 09:57:49 angel-desktop gdm[7282]: Autolaunch error: X11 initialization failed.
Mar  4 09:57:49 angel-desktop gdm[7282]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Mar  4 09:57:49 angel-desktop gdm[7282]: Autolaunch error: X11 initialization failed.
Mar  4 09:57:49 angel-desktop gdm[7282]: )
Mar  4 09:58:25 angel-desktop sudo:    angel : TTY=unknown ; PWD=/home/angel ; USER=root ; COMMAND=/usr/bin/nvidia-settings
Mar  4 10:03:23 angel-desktop sudo:    angel : TTY=unknown ; PWD=/home/angel ; USER=root ; COMMAND=/usr/bin/nautilus
```

---

### Post by Ms_Angel_D on 2009-03-04
> **heindsight said:**
> Actually it's the sudoers file, located at /etc/sudoers.

The command to edit the file is visudo, run it like:
```
sudo visudo
```

If you just want to inspect the contents of the file, without changing it, do:
```
sudo cat /etc/sudoers
```

ok but what exactly am I looking for...lol.

---

### Post by heindsight on 2009-03-04
> **MetalHellsAngel said:**
> ok but what exactly am I looking for...lol.

I'm not really sure actually :) perhaps you can post the contents of your sudoers file here, then we can see if there's anything unusual going on in there...

The default sudoers file should look something like:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

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
```

---

### Post by Ms_Angel_D on 2009-03-04
hmmm seems to be what I have. 

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

---

### Post by Slim Odds on 2009-03-04
So.... did you wait a while?......

It's about 10 or 15 minutes where it remembers your password... I don't remember exactly.

For example:```
sudo apt-get update && sudo apt-get upgrade
```will only ask for your password **once**.

And, if you do it again right way, it will **not ask** for your password at all.

---

### Post by Ms_Angel_D on 2009-03-04
> **Slim Odds said:**
> So.... did you wait a while?......

It's about 10 or 15 minutes where it remembers your password... I don't remember exactly.

For example:```
sudo apt-get update && sudo apt-get upgrade
```will only ask for your password **once**.

And, if you do it again right way, it will **not ask** for your password at all.

It's not actually at the command line where this occurs it's if I say

gksu nvidia-settings

or gksu nautilus

---

### Post by Slim Odds on 2009-03-04
> **MetalHellsAngel said:**
> It's not actually at the command line where this occurs it's if I say

gksu nvidia-settings

or gksu nautilus

Those still work the same way.......

Log out... go have a sandwich... come back... try it again....

---

### Post by chriskin on 2009-03-04
> **MetalHellsAngel said:**
> hmmm seems to be what I have. 

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (**Note that later entries override this,** so you might need to move
# it further down) [B]
# %sudo ALL=NOPASSWD: ALL[/B]

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

your sudoers list shows that it will have to ask you for a password
what happened after you waited a while or rebooted?

---

### Post by sisco311 on 2009-03-04
by default, the sudo timestamp is valid for 15 minutes,
try to remove it and run the command again:
```
sudo -K 
gksu nautilus
```

"sudo -K" does not require a password. gksu should ask you for your password.

also make sure you are not logged in as root:
```
whoami
```

---

### Post by Ms_Angel_D on 2009-03-05
I feel so goofy, I guess after being up all night working on an install on another comp, I was just out of patience. Everything seems to be ok. Thanks to all those that replied though I do appreciate the effort :D.

---

