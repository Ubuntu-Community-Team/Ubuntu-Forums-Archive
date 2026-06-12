---
title: "[SOLVED] Looked myself out of Sudo'ing in Xubuntu??"
date: 2008-12-09
forum: General Help
---

### Post by freshtealeaf on 2008-12-09
I was trying to get VirtualBox working and I was following [this]("http://forums.virtualbox.org/viewtopic.php?t=3776") guide online.

```

usermod -G vboxusers your_username
(now "cat /etc/group" again to see the change) 
```

After I entered this command into xterm and logged out and back in with my user name, I can no longer run sudo commands. 

```

aries@aeonlinux:~$ sudo apt-get something
[sudo] password for aries: 
aries is not in the sudoers file.  This incident will be reported.
aries@aeonlinux:~$ 
```

Any help here? I'd really like to sudo again.. :( 

I'm using Xubuntu, no clue what version. I think 8.04 or 8.10.. Linux kernel 2.6.24-22-generic.



[B][U]UPDATE!
[/U][/B]
I fixed it.

I booted into recovery mode, went to the shell prompt and typed in

```
usermod -a -G admin aries
exit
```

It worked, thankfully!

---

### Post by sisco311 on 2008-12-09
Reboot the compuer and select the *recovery mode* from the grub menu.
Wait for the *recovery menu* and select the *root shell* option.

Add your user to the admin group:
```
adduser *username* admin
```
(replace *username* with your log in name)
type:
```
exit
```
and choose to resume a normal boot.

[http://www.psychocats.net/ubuntu/fixsudo]("http://www.psychocats.net/ubuntu/fixsudo")

EDIT
next time use:
```
usermod -**a**G *group* your_username
```
(-a = *Add the user to the supplemental group(s). Use only with -G option.*)
or
```
adduser *your_username* *group*
```
to add a user to a group.

---

