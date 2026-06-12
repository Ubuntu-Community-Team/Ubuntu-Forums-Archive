---
title: "get ssh to cache certificate creds."
date: 2006-02-07
forum: Desktop Environments
---

### Post by dguido on 2006-02-07
I've got ssh certificate logins set up with all my machines so my public key is in all their /home/user/.ssh/authorized_keys files.  I'd like it so that Ubuntu loads my ssh key at login to ssh-agent and lets me login without typing a password.

I used to be able to do this with Gentoo and keychain because I'd log in to text mode, instead of gdm and gnome.  With Ubuntu, keychain seems to never get called on startup when I put it in my bash_config and it never seems to remember my keys once I do it manually.

Can someone provide a step by step walkthrough of how to get the setup I described, with or without keychain?

---

### Post by bugmenot on 2006-02-07
Not sure if this is what you need or not, but take a look at the startup tab of gnome-session-properties

---

### Post by dguido on 2006-02-08
Well yes probably, but that doesn't solve the problem of keychain being a text mode program.  When will it prompt me for passwords to my keys?  If it blocks the startup of my machine thats a bad thing.  Is there a graphical keychain app?

---

### Post by cwaldbieser on 2006-02-08
[QUOTE=dguido]Well yes probably, but that doesn't solve the problem of keychain being a text mode program.  When will it prompt me for passwords to my keys?  If it blocks the startup of my machine thats a bad thing.  Is there a graphical keychain app?[/QUOTE]
I would guess that the gnome-keyring-manager package is what you want, though I have never used it myself.

---

### Post by dguido on 2006-02-08
I just tried it.  It's half baked.  There's no documentation on how it works or even exactly what it does.  You can't add keys to it.  Basically, it just won't do.  Does Gnome have anything else?

---

