---
title: "Gnome Keyring for root"
date: 2011-03-05
forum: Desktop Environments
---

### Post by 448191 on 2011-03-05
Hi, how do setup a Gnome Keyring for the root user?

---

### Post by vanadium on 2011-03-05
You don't. The root account is disabled on an Ubuntu system, so it makes no sense to set up the gnome keyring for the root account. Even if you'd enable the root account, it would be a very bad idea to log into a graphical session as root.

---

### Post by 448191 on 2011-03-05
Well, I need to run subversion as root. I can edit /root/.subversion/config and make it use gnome-keyring or kwallet. kwallet doesn't remember anything, and gnome-keyring does nothing, which is not surprising as there is no keyring set up for root.

I have a script that does multiple svn exports, re-typing my password is annoying and slow, and storing plain text is not an option.

---

### Post by vanadium on 2011-03-05
There is the "sudo -i" command that provides you a terminal with a root environment. This should be all you need for performing activities as root.

---

### Post by 448191 on 2011-03-05
> **vanadium said:**
> There is the "sudo -i" command that provides you a terminal with a root environment. This should be all you need for performing activities as root.

Sigh... Yes, I am using sudo -i. This is not my first day on ubuntu.

Are you done with the obligatory introductions, so we focus on what I am asking: getting a keyring for the root user?

---

### Post by vanadium on 2011-03-05
It is quite important for other users to realize that this is not recommended practice. This concludes my obligatory introductions.

Now it might be a good idea to tell what you already did/tried, so people can help you. My first impression is that enabling the root account and logging into the graphical environment as root should already do the trick on its own.

---

### Post by 448191 on 2011-03-05
Oddly enough that does work when logging into the root account but not with sudo -i.

So subversion is looking at the config for root but somehow the keyring is not available when using sudo.

---

### Post by vanadium on 2011-03-05
For gnome-keyring to work, the user must be logged in onto the gnome graphical desktop environment.

---

### Post by 448191 on 2011-03-05
Hmokay.. Should I conclude that it isn't possible?

Or perhaps there is a way to use the regular user's keyring when sudoing?

---

### Post by vanadium on 2011-03-05
I am not sure why you would need gnome-keyring for what you want to do. Gnome-keyring provides a storage for keys to users logged in on the gnome desktop. You seem to want to use it for something else.

---

### Post by 448191 on 2011-03-05
Maybe I'm being vague but it seems pretty obvious with the information I provided.

I want to use a script that does svn exports, as root, using sudo, without having to type the svn password multiple times.

---

