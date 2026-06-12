---
title: "gnome-keyring and some apps expecially network-manager"
date: 2006-01-03
forum: Desktop Environments
---

### Post by joneZ on 2006-01-03
Hi,

Decided to switch from wifi-radar to network-manager because the new version (0.5.1) is now in dapper and the old one haven't work so well for me.

One thing that I don't find very good is that, when you log in every time nm-applet access the
keyring-manager an ask's for the password.

Now my question is, can I say for example "Trust nm-applet and do not ask for password"

I would not like to disable the keyring-manager only for some apps.

I haven't found any switch to disable password or always trust any applications.


THX
Erik
Maybe some know's

---

### Post by vayde on 2006-02-16
I have the same problem.  It's really annoying.

Did you ever find a solution?

---

### Post by zorkerz on 2006-11-15
I'm with you guys it seems like many people have this and related problems with the keyring manager.

---

### Post by guruofquality on 2006-11-17
I have been annoyed by this gnome-keyring password thing for too long. The only reason I use it for for network manager. So I "hacked" the source...

Here is my version of the source: [http://www.ece.jhu.edu/~jblum/gnome-keyring-0.6.0-2.tar.gz]("http://www.ece.jhu.edu/~jblum/gnome-keyring-0.6.0-2.tar.gz")

I changed the gnome-keyring-ask so that it checks a file called $HOME/.nm-password. If the name of the keyring is in .nm-password, the keyring will read the password (plain text) from .nm-password rather than prompting the user.

.nm-password has 2 lines:
keyring:keyring_name(usually default)
password:keyring_password(plain text)

If anyone is sick of this network manager password problem and doesnt mind the small security issues, give my source a try.

---

### Post by guruofquality on 2006-11-17
...And here is the a deb file for my hacked gnome keyring:

[http://www.ece.jhu.edu/~jblum/gnome-keyring_0.6.0-0ubuntu2_i386.deb]("http://www.ece.jhu.edu/~jblum/gnome-keyring_0.6.0-0ubuntu2_i386.deb")

Maybe it will help someone somewhere.

---

### Post by k@y@ on 2007-02-09
Can you please make a new package for feisty or for keyring version 0.7+ ?

---

