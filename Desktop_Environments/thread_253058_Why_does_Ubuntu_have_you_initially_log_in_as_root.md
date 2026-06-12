---
title: "Why does Ubuntu have you initially log in as root?"
date: 2006-09-07
forum: Desktop Environments
---

### Post by Rusty Shackleford on 2006-09-07
This seems so counter to Linux, and more of a Windows thing. Or am I missing something?

The install only allowed one account to be set up, so this must be the root. This is not user friendly or safe, since a novice won't know to create a non-root account for daily access.

I am just trying this out, coming over from SuSe 10.1, and I must say I am totally not blown away. No choice in what to install, doesn't allow to to access windows partitions by default, ect.

Suse is ready to go the second you install it. Nearly everything you will want is installed and configured during the install. No xgl, no superkaramba that I can see so far. Yeah, having to download it after the install is very user unfriendly. Even odds that this will be uninstalled by this sunday. :cry: 

I know most of this is a rant, but if someone could answer my question about root I would appreciate it.

Also, is there a way to just have one bar on the menu? Having one on top and bottom is annoying as hell. I am new to gnome, so never had to deal with this.

---

### Post by aysiu on 2006-09-07
You don't understand what's going on. Ubuntu doesn't log you in as root. It logs you in as user. The first user belongs to a group called *admin* that has the ability to temporarily assume root privileges with a password authentication.

Read more here:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

### Post by Rusty Shackleford on 2006-09-07
Ok, fair enough, but the root password is the same for this user.

Very very poor.

---

### Post by aysiu on 2006-09-07
> **Rusty Shackleford said:**
> Ok, fair enough, but the root password is the same for this user.

Very very poor.
It's not the root password. Please--read the link I posted. It's not "very very poor" at all.

---

### Post by stmiller on 2006-09-07
That initial account made during the install is your USER account.

The root account is DISABLED by default in ubuntu. The same as in OS X. There is no root account. Yes you can do sudo (as you can in OS X) to make changes. This is the most secure way to do things.

See the man page for sudo, the parts about security. And welcome to Linux.

---

### Post by whizbaby on 2006-09-07
What stmiller says is simply not true[-( , there actually *is* a root account (look in the list of all users on the system. how could you **sudo passwd** if it doesn't exist?), only nobody knows the (random-generated) password.

---

### Post by Rusty Shackleford on 2006-09-07
> **stmiller said:**
> That initial account made during the install is your USER account.

The root account is DISABLED by default in ubuntu. The same as in OS X. There is no root account. Yes you can do sudo (as you can in OS X) to make changes. This is the most secure way to do things.

See the man page for sudo, the parts about security. And welcome to Linux.

I have done a few things that asked for a root password, and it is the EXACT same password the account that was created during install. That means the same password to access my account is the same one to gain root priveleges. This is VERY unsafe and not user friendly. SUSE 10.1 is miles ahead in user-friendliness. I also had to just switch over to OpenDNS because my connection was at a crawl.

I try to sudo and it won't accept that password, problem is the install process only asks to enter one password. A proper install asks for root password and name and password for one account.

---

### Post by whizbaby on 2006-09-07
Ubuntu is not less user-friendly just because you don't get the *sudo* concept right. I think aysiu mentioned a page...
(excuse me, but what you write suggests you didn't (carefully) read it)

---

### Post by hc2995 on 2006-09-07
basicly you use sudo to preform all the things you need root to do and if it asks for a password its normally YOUR PASSWORD root dosent have  password onless you do sudo passwd root PASSWORD

---

### Post by Rusty Shackleford on 2006-09-07
It is still cheesy. The same password to log in, and the password to sudo should never be the same. Yet, this is the default behavior for Ubuntu.

---

### Post by whizbaby on 2006-09-07
What is the difference in security? If your user account is cracked the root password will be spyed out the next time you do su, so no additional security by having two passwords (the one leads to the other). A user knowing the root password is as dangerous as a user typing sudo and being in the admin group.

---

### Post by aysiu on 2006-09-07
Let's look at some scenarios here:

**One user in Ubuntu**
Operates as user most of the time
Enters a password to perform a root function for a limited period of time

**One user in SuSE**
Operates as user most of the time
Enters a password to become root for all functions for a limited period of time

Not much difference there. Ubuntu seems to come out ahead, though, as it allows you to become root for only a particular function. In SuSE if you log in as root, you can do whatever the hell you want with root privileges... even by accident.

**Multiple users for Ubuntu**
Only those who belong to the *admin* group can perform functions as root. People can be added to or taken away from the *admin* group at any time. If someone is taken out of the *admin* group, she no longer has root access.

**Multiple users for SuSE**
Everyone has a user account. Some users know the root password. If someone is to be taken out of the root group, the root password must be changed and all the other users who know the root password have to be educated about what the new password is.

Ubuntu seems to come out ahead here, too. Everyone has her own password. No one needs to unlearn a password in order to keep things secure.

So why is *sudo* more dangerous? Answer--it isn't. You just don't understand it. Read the link I posted earlier. If you still don't have a clue, I would encourage other people to just ignore you. You're really getting upset about nothing.

---

### Post by Jason.TJ.Johnson on 2006-09-07
Rusty, it seems to me that you're looking for issues with Ubuntu. It seems to me that Ubuntu is more secure out of the box them Suse. Hmm.

---

### Post by stmiller on 2006-09-08
The root account is disabled by default in ubuntu. 

If you don't understand/believe me, open a terminal, and type
su root

to change to root. It will not let you. Try whatever password you'd like to.

Yes, you can get a root shell by doing
sudo bash
etc.

But for the record, you cannot log into the machine as root in ubuntu (or OS X).

> What stmiller says is simply not true , there actually is a root account (look in the list of all users on the system. how could you sudo passwd if it doesn't exist?), only nobody knows the (random-generated) password.

Yes, but it is not enabled. There are many 'users' to Linux. Open up the Users and Groups control panel and click on show all users and groups. You'll see the many "users." It's sort of complicated, but this is Linux.


[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You can make sudo ask for a root password, instead of a user password if you are paranoid. See above link.

[http://ubuntuguide.org/wiki/Dapper#User_Administration](http://ubuntuguide.org/wiki/Dapper#User_Administration)

This entire way of doing things with sudo is the default security way for OS X, also. Sorry you don't like it Rusty, but you can enable root by doing the steps at my above links. Linux is Linux, and you can make Suse or Ubuntu however you like it.

---

