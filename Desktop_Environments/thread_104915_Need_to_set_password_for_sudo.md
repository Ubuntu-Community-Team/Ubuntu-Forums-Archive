---
title: "Need to set password for sudo"
date: 2005-12-17
forum: Desktop Environments
---

### Post by peterthebike on 2005-12-17
Somehow I have managed to "lose" the password for sudo.

When I login there is the correct username/password sequence, but whenever I use sudo or gksudo I do not get asked for a password.

I have checked and /etc/sudoers does not have ```
system_username ALL=(ALL) NOPASSWD: ALL
```
How can I make sudo ask for a password again?

---

### Post by kaamos on 2005-12-17
So running this:
```

sudo -K
sudo echo "testing sudo"

```
Doesn't ask you for a password?

Can you post the sudors file here?

---

### Post by kosmic on 2005-12-17
[quote=peterthebike]Somehow I have managed to "lose" the password for sudo.
 
When I login there is the correct username/password sequence, but whenever I use sudo or gksudo I do not get asked for a password.
 
I have checked and /etc/sudoers does not have ```
system_username ALL=(ALL) NOPASSWD: ALL
```
How can I make sudo ask for a password again?[/quote]
 
 
 
Just remove the NOPASSWD: ALL from the sudoers file

---

### Post by kaamos on 2005-12-17
[QUOTE=kosmic]Just remove the NOPASSWD: ALL from the sudoers file[/QUOTE]
You might want to read the first post again :)
[QUOTE=peterthebike]I have checked and /etc/sudoers does **not** have[/quote]

---

### Post by peterthebike on 2005-12-17
[QUOTE=kaamos]So running this:
```

sudo -K
sudo echo "testing sudo"

```[/QUOTE]
Gives me:
```
peter@ubuntu:~$ sudo -K
peter@ubuntu:~$ sudo echo "testing sudo"
testing sudo
peter@ubuntu:~$
```
[QUOTE=kaamos]So running this:
Can you post the sudors file here?[/QUOTE]
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

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL
```

---

### Post by jaywatkins on 2005-12-17
Can you use the "passwd" command to reset the password, as you would when you first installed?

-J

---

### Post by peterthebike on 2005-12-17
[QUOTE=jaywatkins]Can you use the "passwd" command to reset the password, as you would when you first installed?[/QUOTE]
Reset password - no change. :(

---

### Post by kosmic on 2005-12-18
[quote=kaamos]You might want to read the first post again :)[/quote]
 
 
Eheheeh sorry :)
 
 
Hum and if you restart the system in safe mode ?

---

### Post by peterthebike on 2005-12-18
[QUOTE=kosmic]Hum and if you restart the system in safe mode ?[/QUOTE]
Do you mean when loggin into GNOME selecting Session>Failsafe GNOME (4th option)?

If was what you meant - still no different. :(

---

### Post by kosmic on 2005-12-18
No when you reboot you pc and get to the grub screen, select the kernel that says safe mode, and you should be in single user as root then you can reset your password. hope it helps

---

### Post by kaamos on 2005-12-18
What is the output of the command "groups"? Saw a thread about this that said that the password was asked because the user was a member of the sudo group..

---

