---
title: "/tmp dir"
date: 2005-12-25
forum: Desktop Environments
---

### Post by cfitz on 2005-12-25
I am a new convert from RH / Fedora distros.  I have noticed that after a shutdow that the /tmp dir is 'cleaned' of anything I may have placed there for tmp storage 

This behavior is new to me coming from  a long term RH / Fedora enviroment.  What controls this behavior? The /etc/profile file?

Pardon my 'newness'. 

TIA for any assistance.

clueless_user

---

### Post by briancurtin on 2005-12-25
i believe it comes from the fact that it is just a temporary directory

i didnt see anything in /etc/profile that has an effect on it, but if you want to store stuff temporarily but keep them past shutdown/restart to make a /temp folder for that purpose

---

### Post by timfrost on 2005-12-25
/etc/init.d/bootclean.sh supplies functions that clear /tmp (and other directories).

The key function, bootclean, is called from /etc/init.d/mountall.sh

If I want a file to exist across a reboot, I will save the file to one of:
/var/tmp
$HOME/tmp

---

### Post by cfitz on 2005-12-25
timfrost,

Thank you for your post.  As mentioned in my initial post, I am moving from a RH / Fedora environment.  The behavior, concerning the 'cleaning' of the /tmp dir, after a reboot or shutdown is a new experience for me.

I will take a look at the fle you referenced in your post.

Again, thank you.

cfitz

---

