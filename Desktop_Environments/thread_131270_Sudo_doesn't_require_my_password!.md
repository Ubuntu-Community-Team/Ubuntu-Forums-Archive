---
title: "Sudo doesn't require my password!"
date: 2006-02-16
forum: Desktop Environments
---

### Post by katiad on 2006-02-16
Got an odd problem, not sure when it started, but I'm just now noticing that sudo does not require my password. I /do/ have to type sudo before commands (i.e. sudo mount -a, because simply mount -a demands that only root can do that) but then the job is done. No password required. I have a feeling this isn't, uh, normal.

And it never requires the password - not just a case of sudo hanging around for 15 minutes. What the heck did I do? More, how can I fix it?

---

### Post by codejunkie on 2006-02-16
[QUOTE=katiad]Got an odd problem, not sure when it started, but I'm just now noticing that sudo does not require my password. I /do/ have to type sudo before commands (i.e. sudo mount -a, because simply mount -a demands that only root can do that) but then the job is done. No password required. I have a feeling this isn't, uh, normal.

And it never requires the password - not just a case of sudo hanging around for 15 minutes. What the heck did I do? More, how can I fix it?[/QUOTE]
run ```
export EDITOR=gedit && sudo visudo
```
look for something like this
```
anything	ALL=(ALL) NOPASSWD: ALL
```
and change it to 
```
anything	ALL=(ALL) ALL
```
save and close gedit and try sudo again 
NOTE:this might require you to logout and back in for it to work.

---

### Post by thesnowysoviet on 2006-02-16
[QUOTE=codejunkie]run ```
export EDITOR=gedit && sudo visudo
```
look for something like this
```
anything	ALL=(ALL) NOPASSWD: ALL
```
and change it to 
```
anything	ALL=(ALL) ALL
```
save and close gedit and try sudo again 
NOTE:this might require you to logout and back in for it to work.[/QUOTE]

I'm experiencing the same problem.  Interestingly enough, I get a password prompt for "su - root" but not for "sudo su - ".  I edited the sudoers file as per instructions above, but the problem is still there.

---

### Post by katiad on 2006-02-16
Hmm. This is what I get in the sudoers file:

> 
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

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin	ALL=(ALL) ALL


Don't see anything with the NOPSSWD function....

---

### Post by codejunkie on 2006-02-20
[QUOTE=thesnowysoviet]I'm experiencing the same problem.  Interestingly enough, I get a password prompt for "su - root" but not for "sudo su - ".  I edited the sudoers file as per instructions above, but the problem is still there.[/QUOTE]
did you do an expert install? if so it will enable the root account and not use sudo.

---

### Post by codejunkie on 2006-02-20
[QUOTE=katiad]Hmm. This is what I get in the sudoers file:



Don't see anything with the NOPSSWD function....[/QUOTE]
well this is weird try running ```
sudo -k
``` in the terminal and then try using something that requires sudo like synaptic now it should ask you for the password.

---

### Post by katiad on 2006-02-20
Just attempted that. Ran:  sudo -k  and the command was accepted, but it still refuses to ask for a password.

---

### Post by codejunkie on 2006-02-20
[QUOTE=katiad]Just attempted that. Ran:  sudo -k  and the command was accepted, but it still refuses to ask for a password.[/QUOTE]
im lost then, i've never seen this happen, where sudo would not ask for the password like that, and the user had not set it to do this. maybe someone else here has went through this and has an answer but im kinda stumped on this one.

---

### Post by katiad on 2006-02-20
Heh. Well, thanks anyway. *lol* I fear I can manage to break just about anything. At least no one but me uses this computer.

---

### Post by codejunkie on 2006-02-20
i don't know if this will fix it but click on System/Administration/Users And Groups click on the groups tab check show all users and groups, then the root group and click properties make sure your user name isn't in there.

---

### Post by katiad on 2006-02-20
Nope. Not there.

---

### Post by codejunkie on 2006-02-20
well i don't know what could be causing it sorry i couldn't be more help.

---

### Post by codejunkie on 2006-02-20
i think i might have found it open a terminal and enter 
```
sudo users-admin
```
click on the groups tab then check show all users and groups, scroll down till you find ```
sudo
``` click on properties and if your username is listed remove it.

---

### Post by Jucato on 2006-02-20
Does this behavior remain even after you reboot? or it disappears after rebooting then misbehaves again after a few sudo (w/ password prompt) commands?

---

### Post by jerrykenny on 2006-02-20
I'm having the same problem with a Kanotix installation (which is really debian Sid) . . . . its a bit worrying,  I've edited the sudo file with the command

visudo

If you want to just have a look at the syntax, try

nano /etc/sudoers       (but DONT edit it with NANO)

I'm a bit suspicious 'though of the permissions I've set in the "kuser" GUI . . . . 

 I had added the offending user account to the "bin" group, have since removed that privelidge . . . . 

Reckon its a good time to have a firewall . . . .

---

### Post by katiad on 2006-02-20
[QUOTE=codejunkie]i think i might have found it open a terminal and enter 
```
sudo users-admin
```
click on the groups tab then check show all users and groups, scroll down till you find ```
sudo
``` click on properties and if your username is listed remove it.[/QUOTE]


Got it!! Hurrah! It works as normal now.

---

### Post by thesnowysoviet on 2006-02-27
[QUOTE=katiad]Got it!! Hurrah! It works as normal now.[/QUOTE]

sudo: users-admin: command not found

:(

---

