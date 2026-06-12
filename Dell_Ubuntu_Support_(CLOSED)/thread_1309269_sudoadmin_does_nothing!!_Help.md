---
title: "sudo/admin does nothing!! Help??"
date: 2009-11-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Ubermench on 2009-11-01
for instance 

I enter

user@laptop:~$sudo sh-do-this.run
[sudo] password for user
#entered password <nothing> hit return
user@laptop:~$
#No result

It's as if I never typed anything in at all, can't upgrade, it won't let me. Can't install new/better drivers. cant DL/install anything. Suggestions?

I've just installed Ubuntu Desktop 9.04 on a Dell Inspiron 1720 that was built for Vista (but I installed XP pro). Now moved over to pure Ubuntu. I know a little but not a lot so please take it easy and treat me as a new user?? 
 Thanks

---

### Post by sisco311 on 2009-11-01
please post the output of:
```
id
```
and
```
sudo cat /etc/sudoers
```

---

### Post by Ubermench on 2009-11-01
daddy@Lappy:~$ id
uid=1000(daddy) gid=1000(daddy) groups=4(adm),20(dialout),24(cdrom),46(plugdev),106(lpadmin),121(admin),122(sambashare),1000(daddy)
daddy@Lappy:~$ sudo cat /etc/sudoers
[sudo] password for daddy: 
daddy@Lappy:~$ 

seems as though any sudo command does nothing..

---

### Post by sisco311 on 2009-11-01
Reboot the computer and select Recovery Mode from the grub menu.

You may have to press the Escape key during bootup in order to see the menu.

Wait for all the boot-up processes to finish.

Select *Drop to root shell prompt* option from the Recovery Mode menu.

Edit the sudoers file:
```
EDITOR=nano visudo
```
and make sure that looks like this:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
**%admin ALL=(ALL) ALL**
```

to save the file and exit press Ctrl+x, y, Enter

type:
```
exit
```
and choose to resume a normal boot.

[http://psychocats.net/ubuntu/fixsudo]("http://psychocats.net/ubuntu/fixsudo")

---

### Post by Ubermench on 2009-11-01
OK file look identical however.. when it asked for a password I entered the password I *tried* to change the sudo account to and it worked.. 
so
back to desktop, try to use *that* password and 

daddy@Lappy:~$ sudo sh NVIDIA-Linux-x86-173.08-pkg1.run
[sudo] password for daddy: 
Sorry, try again.
[sudo] password for daddy: 
Sorry, try again.
[sudo] password for daddy: 
Sorry, try again.
sudo: 3 incorrect password attempts
daddy@Lappy:~$

so, can't use add/remove, synaptic or anything that requires admin rights. Its as if I never entered the command in the first place.

---

