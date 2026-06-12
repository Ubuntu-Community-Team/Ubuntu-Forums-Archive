---
title: "I just deleted my sudo account!"
date: 2006-06-04
forum: Desktop Environments
---

### Post by george_apan on 2006-06-04
OK I admit that was stupid. I just deleted the account I created when installing dapper and I'm left with an account with no sudo privileges. While I thought that a new user I had created had sudo privileges, it seems that was not the case. Is there something I can do to get sudo access back?

---

### Post by taurus on 2006-06-04
Only the original user that you've created during the installing process has the root's privillage unless you specific for other users later.  I guess you boot your machine and at the GRUB screen, pick the recovery mode (or single user mode) and it will dump you into a console as root.  Now, create a new account with useradd command and make sure you add that user to groups adm and admin in /etc/group.  Reboot and all is good again...  ;)

---

### Post by etank on 2006-06-04
Someone correct me if I am wrong but shouldn't you be able to use the live CD to mount the / partition and them edit /etc/group and add the new user to the admin group.

---

### Post by taurus on 2006-06-04
Yeah, you can use the desktop CD to boot from and edit it but if you don't want that account to have access to sudo but rather want to create a new one...

---

### Post by lofty00 on 2006-06-04
[QUOTE=etank]Someone correct me if I am wrong but shouldn't you be able to use the live CD to mount the / partition and them edit /etc/group and add the new user to the admin group.[/QUOTE]

This should work. Just add the username at the end of the 'admin:x:112:' line. In case you screwed up your /etc/sudoers file (as I did), here's a copy of mine (from a fresh install of Dapper Drake.)

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
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

---

### Post by george_apan on 2006-06-05
Thanks everyone! I edited the /etc/group file with the live CD and it's all fixed now. :)

---

### Post by jgcamp99 on 2006-06-05
This would be why one of the first things I did was re-enable root (administrator) to be able to log into gnome. Ubuntu is the first Os that I've run into where root can't login by default. I found copying and pasting a couple of Flash Macromedia 7 player plugins for a manual install required that I be "root" to copy them to that directory. Sudo is secure, but when you're setting up a system and applications go on dirty like they do in Linux (nothing ever works the first time outside of what Ubuntu has available thru the installation apps, but that's not everything I want to install). You need total access to the folders and system.

Another example of a dirty install, Citrix ICA Client, Citrix needs Open Motif 2.2.*, you can get that easily thru Ubuntu. Then get Citrix from their website, but without that version of Open Motif, Citrix won't work. Try copying to certain folders, Ubuntu/Linux won't allow it, that's why you need to be root.

---

### Post by Ramses de Norre on 2006-06-05
All that can be done through sudo or (gksudo if you want a gui)..

---

