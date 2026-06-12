---
title: "Can't make login keyring passwordless -- Seahorse won't accept blank password"
date: 2013-05-08
forum: Desktop Environments
---

### Post by noah++ on 2013-05-08
Hi,

I'm using a full-disk encryption password, so I configured gdm for automatic login. That works, but Gnome keeps prompting me for my password to unlock the login keyring. I don't want that.

To make my keyring passwordless, I tried entering a blank new password in the Passwords and Keys applet, also known as Seahorse. Several online help sources suggested that avenue to a passwordless keyring, and I can't find any that give another method. However, I am having exactly the same problem [this person on the Arch forums has]("https://bbs.archlinux.org/viewtopic.php?id=162963"). It won't accept a blank password.

Suggestions? Is there away to get this done in the CLI? I'm in Ubuntu 13.04.

---

### Post by noah++ on 2013-05-08
Right after I posted that, I found [a python one-liner]("http://askubuntu.com/a/187720") that worked for me.

---

