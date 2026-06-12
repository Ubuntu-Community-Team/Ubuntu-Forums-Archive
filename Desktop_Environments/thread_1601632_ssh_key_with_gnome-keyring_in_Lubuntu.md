---
title: "ssh key with gnome-keyring in Lubuntu"
date: 2010-10-20
forum: Desktop Environments
---

### Post by leorolla on 2010-10-20
Hi folks,

I'm trying Lubuntu for my low-resource netbook and I'm lovin' it.

But I can't get my ssh key passphrase work with the keyring manager.

I even created a new user account with a fresh home directory and it doesn't work. You run "ssh [email]myname@mydomain.net[/email]" and it prompts you for the key passphrase in the terminal.

Expected behavior: with Gnome, you run "ssh [email]myname@mydomain.net[/email]" and the password manager opens a GUI to ask for the passphrase. Once unlocked, it remains unlocked until you log off. Moreover, at that moment of unlocking you can tell it to remember the passphrase forever so it gets automatically unlocked next time you login.

The keyring works fine for the wireless password, and for luks-encrypted volumes, but not for Secure Shell keys.

Has anyone managed to get it working?

I'm using Ubuntu Lucid, installed lubuntu-desktop package, using gdm session manager, all updated.

Thanks in advance!

---

### Post by kongo09 on 2011-01-14
Similar question, also no answer:
[http://ubuntuforums.org/showthread.php?t=1661501](http://ubuntuforums.org/showthread.php?t=1661501)

---

