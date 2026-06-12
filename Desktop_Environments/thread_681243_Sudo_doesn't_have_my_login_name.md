---
title: "Sudo doesn't have my login name"
date: 2008-01-28
forum: Desktop Environments
---

### Post by cliffr on 2008-01-28
This concerns a new Ubuntu Server 7.10 install. The installation went 
well but it boots to a command line. That would be ok but the books I bought all refer to Nautilus which is used to start new application installations.
But when I try to install Nautilus or anything else with sudo, I get a message that tells me my login name is not in the sudoers file and that I will be reported.
The books all say to use Visudo tool to edit the sudoers file but that too has
to start with sudo. I feel like the perverbial "Catch 22" has me in it's grip. Can
anyone shed some light on this or at least recommend a book?

---

### Post by mouseboyx on 2008-01-28
Yes, you have to login to root on the server, type su and login with the root password, which is root if you haven't changed it.

---

### Post by qpieus on 2008-01-28
Normally in ubuntu, to use sudo your username must belong to the admin group. I suspect it does not in your case. You can find out by typing ```
id
``` at the command prompt. Somewhere in the output look for the admin group. I bet you won't find it. To add yourself to the admin group you need to boot into recovery mode. Recovery mode should be one of the choices on the grub boot menu. Once in recovery mode, you'll be at a root prompt. Type:```
adduser *username* admin
``` This should add your username to the admin group. Reboot into normal mode and your sudo should then work.

---

### Post by cliffr on 2008-01-28
I entered "su" and got 
Password:
Entered "root" and was rejected.
During the installation the install process recommended that I
enter my first and last name, then my first name for login
and then a password. I tried the password after again entering
"su" and again was rejected. Could the root password have 
been changed in Distro 7.10?
Thanks for the reply.

---

### Post by Fraktyl on 2008-01-29
I'm not sure what the root password is by default in 7.10.

Your best bet is to qpieus suggested.  If you don't have an option in your grub menu for Recovery mode what you'll have to do is this:

When grub comes up, hit 'e' to edit the boot process.

Highlight the line that has kernel on it (should be the second line).  Hit 'e' again to edit that line.  Change the end so instead of

ro quiet splash

It should look like

ro single

This will boot you into recovery mode with an automatic root shell.   You should have the recovery option already though if it's a fresh install and you haven't messed with the menu.lst file for grub.

I actually wouldn't use useradd.  Try this:

usermod [yourusername] -G admin

---

### Post by qpieus on 2008-01-30
From the ubuntu community docs:> By default, the root account password is locked in Ubuntu. This means that you cannot login as root directly or use the su command to become the root user, however, since the root account physically exists it is still possible to run programs with root-level privileges.This is where sudo comes in; it allows authorized users (normally "Administrative" users; for further information please refer to AddUsersHowto) to run certain programs as root without having to know the root password.
That's why su didn't work for you. And sudo is not working for you because you probably are not in the admin group. You need to add yourself to the admin group. There are a few ways to do that, but the easiest way is what I described earlier. Here's the link to the sudo community documentation:  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by cliffr on 2008-02-03
My thanks to mouseboyx, qpieus, and Fraktyl.
I was able from "root" to use visudo to edit sudoers to add my
login name to the list. and now "sudo" works on everything!
How many beans can you use before getting removed?
cliffr

---

