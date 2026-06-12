---
title: "Default root password?"
date: 2006-08-15
forum: Desktop Environments
---

### Post by JeanNiBee on 2006-08-15
Hi

First time installer of Ubunto here (i'm no guru but I' installed other Linux 
flavours before)

This install never asked to setup a root account, and I can't find 
documentation telling me the default root password.

Any help would be appreciated. Thanks.

---

### Post by kebes on 2006-08-15
Ubuntu is a bit different than other distros in regards to the root account.

By default there is not root account. However the first user you create has "root privileges" which means that you can do root-like things when you want. In particular, the command "sudo" allows you to run a single one-line command with "superuser power". So, for example, if you try to install software by typing:
$ aptitude install apache2
It will give you an error. If you add sudo:
$ sudo aptitude install apache2
It will ask for your password and then continue properly.

You can also use "sudo -s" to jump into a root shell, which is essentially the same thing as switching into root in a conventional unix environment.

There are many reasons that Ubuntu decided to do it this way. (More user friendly, arguably more secure without a root account since an attacker must guess username and password, etc.) I'd recommend trying it out and getting used to it. When you create new users, you can decide whether they have root privileges or not (whether or not they belong to the admin group).

If you really want to activate the root account in Ubuntu, there is a way to do this.

Hope that answers your question.

---

### Post by aysiu on 2006-08-15
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by JeanNiBee on 2006-08-15
Wow.. this is great. Thanks for your help.

Makes sense from a security POV too.

---

### Post by monoufo on 2006-08-15
I like having the root account.  Sometimes you want to do several things in root in a row, and commands are often not posted with sudo prefixing them.  I so things the proper ubuntu way most of the time, but a real root account is convienent.  most people don't need all the security.  

sudo passwd

there.  that will set the root password and automatically enable the account.

---

### Post by Ramses de Norre on 2006-08-15
Then do sudo -s or sudo su? That's not much more typing then su..

---

### Post by ardchoille on 2006-08-15
> **monoufo said:**
> I like having the root account.  Sometimes you want to do several things in root in a row, and commands are often not posted with sudo prefixing them.  I so things the proper ubuntu way most of the time, but a real root account is convienent.  most people don't need all the security.  

sudo passwd

there.  that will set the root password and automatically enable the account.

Please do not tell people to enable the root account. It is not supported config and can lead to future problems. If it worked fine for you, it doesn't mean it will work fine for all Ubuntu systems.

When someone tries to break into your computer, they know there is a root account. Disabling the root account makes it much harder to break into and they can't break into user accounts because they don't know which users exist on the system. There are a number of reasons to use sudo/gksudo in Ubuntu and leave the root account disabled:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

