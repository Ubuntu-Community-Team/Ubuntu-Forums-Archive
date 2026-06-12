---
title: "[SOLVED] Different password for sudo?"
date: 2008-12-05
forum: General Help
---

### Post by LinuxView on 2008-12-05
Is it possible to have a different password for the command sudo besides having the user password? My user password is really long and I rather have something short (not too easy) password for the sudo command just to speed things up. Googling brought me to the point where its possible if I add an user to admin but I have no idea how to connect the user and the sudo command. Example of what i'm trying to aachive: Entering "sudo xcommandhere" should let me type the password of "user-i-created-for-sudo-pw" instead of typing the password for the current user logged in. .. is this even possible? Thanks ):P

---

### Post by ohzopants on 2008-12-05
Not really.
But you might want to read the man page for su:
```

man su

```

---

### Post by SomeGayDude on 2008-12-05
sudo is tied to the root password.  That was the one you gave when installing ubuntu.  Then you have your user password.  They can be different.

---

### Post by kerry_s on 2008-12-05
**man sudo**

but why open a potential security hole?

---

### Post by ohzopants on 2008-12-05
sudo is not tied to the root password.

By default there is no root user and therefore there cannot be a root password.  sudo will accept the current user's password as long as that user is a member of the "sudoers" (or maybe "admin", or just "sudo"; I can't remember off the top of my head) group.

---

### Post by SomeGayDude on 2008-12-05
> **ohzopants said:**
> sudo is not tied to the root password.

By default there is no root user and therefore there cannot be a root password.  sudo will accept the current user's password as long as that user is a member of the "sudoers" (or maybe "admin", or just "sudo"; I can't remember off the top of my head) group.

Thanks, its been too long since I've had to install ubuntu that I forgot.  But, you could have two administrator accounts.  Kerry_s does have a point, if you have anything worth protecting then don't do this.

---

### Post by LinuxView on 2008-12-05
There really nothing on that computer to protect. It's just a test box I created to mess around with packages before installing them on my computer. Having said that, I did create an another admin user and now my next step would be to default the sudo password to this newly created account's password. How do i do that? I read somewhere that you can default the sudo password to the root user's password. I know it isn't recommend and I understand the risks but I can't seem to find the instructions. Thanks ):P

---

### Post by wirelessmonkey on 2008-12-05
> **ohzopants said:**
> sudo is not tied to the root password.

By default there is no root user and therefore there cannot be a root password.  sudo will accept the current user's password as long as that user is a member of the "sudoers" (or maybe "admin", or just "sudo"; I can't remember off the top of my head) group.

This is false.  There is a root user, but for all intents and purposes it has an invalid/impossible password, hence the need for sudo escalation.

---

### Post by SomeGayDude on 2008-12-05
Ive done some research and didn't find anything.  I don't believe their is a way to bypass sudu which doesn't surprise me.

---

### Post by dagnabit dang doohickey on 2008-12-05
You can always edit the [sudoers]("http://www.sudo.ws/sudo/man/sudoers.html") file (with [visudo]("http://www.sudo.ws/sudo/man/visudo.html")) to extend, or never expire, your sudo timeout.

```

## two hour timeout
Defaults:*username* timestamp_timeout=120

## never expire
Defaults:*username* timestamp_timeout=-1

```

Manually expire sudo with the command: **sudo -k**

---

### Post by kerry_s on 2008-12-05
> **LinuxView said:**
> There really nothing on that computer to protect. It's just a test box I created to mess around with packages before installing them on my computer. Having said that, I did create an another admin user and now my next step would be to default the sudo password to this newly created account's password. How do i do that? I read somewhere that you can default the sudo password to the root user's password. I know it isn't recommend and I understand the risks but I can't seem to find the instructions. Thanks ):P

you use the "-u" command to run as a different user.
example:
**sudo -u user command**

if it's just a toy box, than i'd skip adding another user all together. just add your user to the staff or sudo group and don't bother with passwords. see pic.

**WARNING!!! NOT RECOMMENDED IF SECURITY IS A CONCERN!**

---

### Post by SomeGayDude on 2008-12-05
This is cool.  I will never stop learning  :-)  Have fun.

---

### Post by aysiu on 2008-12-05
[This](http://ubuntuforums.org/showthread.php?p=1053358#post1053358) may help you.

---

### Post by LinuxView on 2008-12-05
> **aysiu said:**
> [This](http://ubuntuforums.org/showthread.php?p=1053358#post1053358) may help you.

Thank you! That's actually what I was looking for and it works perfect. The poster brings up a good point. If the user's password was compromised somehow, they will still need the password of the second user to do any system wide damage. I went a head and disabled the root logins so that newly created root account isn't able to log in. Thanks for the help guys ):P

---

