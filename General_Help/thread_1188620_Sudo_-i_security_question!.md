---
title: "Sudo -i security question!"
date: 2009-06-15
forum: General Help
---

### Post by Coder68 on 2009-06-15
I had forgotten my root password and found a post in the Ubuntu forums that said use ```
sudo -i 
```and that it would run you as root under your (user) password. Well, much to my suprise, it worked!!!

Big questions is, whats to stop any old standard user from running this and changing the root password and running amok!!????

Am I missing something?

I am a total beginner here, so thanks for the help!

Coder68

---

### Post by michy99 on 2009-06-15
It will work for any user with admin privileges. But then, anyone with physical access to your computer has several ways to get to your data. This is true with any operating system.

---

### Post by aysiu on 2009-06-15
> **Coder68 said:**
> I had forgotten my root password and found a post in the Ubuntu forums that said use ```
sudo -i 
```and that it would run you as root under your (user) password. Well, much to my suprise, it worked!!!

Big questions is, whats to stop any old standard user from running this and changing the root password and running amok!!????

Am I missing something?

I am a total beginner here, so thanks for the help!

Coder68
There is no root password in Ubuntu.

There are some user accounts that belong to the *admin* group. Users in that group can use *sudo* to temporarily gain root privileges for certain tasks.

If you are in the *admin* group and want to have a persistent root prompt, you use the command ```
sudo -i
``` This will, for all practical purposes, log you in as root, but you have not by doing this set a root password.

Users who are not in the *admin* group cannot use *sudo* to gain root privileges.

Anyone with physical access to the computer can reset the password of any user account. This is true of any operating system (Linux, Windows, Mac OS X).

---

### Post by Coder68 on 2009-06-15
OK.  Thanks.

I knew that anyone with physical access can do anything they want, but I was shocked to see that a user could gain root this way.

I checked and I am a member of the admin group.

I thought that there were only users and root users in Linux.  I take it that admin is an inbetween level?

When I tried to use su to change to root it ask me for a password.  I tried blank and all my standard passwrods, but could not remember what I made it.  (I built this box back when 6.06 was new, and just never really used it.) Once I had a root prompt, I reset my password.

Why does Ubuntu not have a password for root?  Is'nt this a security issue?

Edit:
>  If you are in the *admin* group and want to have a persistent root prompt, you use the command
How do I undo the presistant root?

Thanks for the quick answers!

C68

---

### Post by aysiu on 2009-06-16
> **Coder68 said:**
> 
I thought that there were only users and root users in Linux.  I take it that admin is an inbetween level? Yes, basically. *sudo* allows for more complex security setups than just user and root. By default, Ubuntu allows anyone in the *admin* group to temporarily escalate to root privileges (after password authentication), but you can fine-tune *sudo* so that a user can escalate privileges on only certain commands... or not require a password at all for certain commands.

> When I tried to use su to change to root it ask me for a password.  I tried blank and all my standard passwrods, but could not remember what I made it.  (I built this box back when 6.06 was new, and just never really used it.) Once I had a root prompt, I reset my password. As I said before, the root account is disabled for login in Ubuntu. It does not have a password. You don't log in as root in Ubuntu.

*su* allows you to switch users. If you don't specify a username, then *su* switches to root. Since Ubuntu doesn't have a root login by default, then obviously it doesn't let you *su* to root. If you need a persistent root login, just use ```
sudo -i
```

> Why does Ubuntu not have a password for root?  Is'nt this a security issue? No, it isn't a security issue. Read this for more details:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> How do I undo the presistant root? Type ```
exit
```

---

### Post by Coder68 on 2009-06-16
Thanks.

I found out you can't log in as root after trying to do so.  

Before I ask about the getting out of a persistant root prompt, I did type exit. That would take me back to me, but when I typed exit again, it wou ld take me back to root. Exit would not exit the shell anymore. Before, exit would just quit the shell.  It appears that I have to click the x in the shells window to close it once I have run the sudo -i.

Thanks again.
C68

---

### Post by aysiu on 2009-06-16
That's weird. I've never seen that behavior before.

---

### Post by mixmaster on 2009-06-16
> **Coder68 said:**
> Thanks.

I found out you can't log in as root after trying to do so.  

Before I ask about the getting out of a persistant root prompt, I did type exit. That would take me back to me, but when I typed exit again, it wou ld take me back to root. Exit would not exit the shell anymore. Before, exit would just quit the shell.  It appears that I have to click the x in the shells window to close it once I have run the sudo -i.

Thanks again.
C68
This is rather peculiar behaviour - I suspect you had stacked several sudo and non-sudo enabled sessions in some way.

For the record, sudo -i is very convenient if you have to issue a significant number of commands with root authority but it is generally a bad thing.  It is too easy to forget to exit and then to later use the sudo session for something inappropriate and dangerous.  Or for someone else to use the session if you leave the machine unattended.

Try to get into the habit of using sudo in single-command mode -
sudo <command>
This will prompt you for your password (ie your normal login password) before executing <command> with root authority.  Subsequent single-line sudo commands will not prompt unless a certain timeout between commands has been exceeded.

---

### Post by Coder68 on 2009-06-16
Mixmaster,

When I opened up a new shell, the behavior went away.

Is sudo any different the su? (Other then su giving you root in your prompt?)

How much time will the login stay good for?

Thank you,

C68

---

