---
title: "Gnome Keyring Manager"
date: 2007-07-02
forum: Desktop Environments
---

### Post by angus.hendrick on 2007-07-02
I have read some other [posts]("http://ubuntuforums.org/showthread.php?t=112225") about the Gnome Keyring Manager asking for a password everytime the user logs in, and how by setting the same password for your login as for the keyring, you can avoid this by making some other configuration changes...  that's not my problem.

My problem (well, the one that's suitable for discussion here), is that I somehow have managed to wind up with a gnome keyring manager that is locked by a password that I don't know.  I don't remember ever setting the password actually, and as best I can recall I'd never seen the keyring manager until I installed the network-manager package under Edgy (which I've now upgraded to Feisty).

I've considered removing the package gnome-keyring-manager with aptitude, but it comes back with a list of dependent packages that's pretty long, and it kinda makes me nervous to rip out something that seems so embedded in the environment, even though I intend to reinstall it (and set the password to something I know).

Any advice?

---

### Post by olifhar on 2007-07-04
Same problem: I found [this post]("http://ubuntuforums.org/showpost.php?p=943443&postcount=7"). Seems to have worked so far!

---

### Post by angus.hendrick on 2007-07-06
I think that worked.  Thanks much!

---

