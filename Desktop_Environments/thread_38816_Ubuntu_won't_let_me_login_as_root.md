---
title: "Ubuntu won't let me login as root"
date: 2005-06-02
forum: Desktop Environments
---

### Post by Paul Panks on 2005-06-02
I don't recall Ubuntu letting me set up a root user, and when I typed the password for my username, root falls to login. I can only login via my user name. And in order to do anything with root capacity, I have to go into a terminal a type "sudo su". Then it asks for my username password, which works.

This is a major pain because I need to setup and update my system, but can't so easily from my main user account.

So how do I change the root password for my system, so I can login as root (from the main login screen)?

Paul

---

### Post by kvidell on 2005-06-02
[QUOTE=Paul Panks]I don't recall Ubuntu letting me set up a root user, and when I typed the password for my username, root falls to login. I can only login via my user name. And in order to do anything with root capacity, I have to go into a terminal a type "sudo su". Then it asks for my username password, which works.

This is a major pain because I need to setup and update my system, but can't so easily from my main user account.

So how do I change the root password for my system, so I can login as root (from the main login screen)?

Paul[/QUOTE]
 try this:
sudo -s
or:
sudo -s -H

They're useful.

Logging in as root from GDM is highly discouraged. I don't mean to insult your intelligence, but it's just not Good Eats(tm).

[http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo) for more (read: better) info.
- Kev

---

### Post by Alexander Kirillov on 2005-06-02
[QUOTE=Paul Panks]I don't recall Ubuntu letting me set up a root user, and when I typed the password for my username, root falls to login. I can only login via my user name. And in order to do anything with root capacity, I have to go into a terminal a type "sudo su". Then it asks for my username password, which works.

This is a major pain because I need to setup and update my system, but can't so easily from my main user account.

So how do I change the root password for my system, so I can login as root (from the main login screen)?

Paul[/QUOTE]
 [http://ubuntuguide.org/#setchangeenablerootpassword](http://ubuntuguide.org/#setchangeenablerootpassword)

---

