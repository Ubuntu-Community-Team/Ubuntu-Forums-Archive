---
title: "Found a new (I think) fix for a problem!"
date: 2005-04-22
forum: Desktop Environments
---

### Post by cmbroth on 2005-04-22
**Found a fix** for a problem with *Unable to run xxxx : Child process ended with result 1*!!

It wasn't that my password was wrong, or the root pw, it was that my username wasn't listed in sudoers file! After correcting this, everything works as it should!! Woohoo! Hope this help all of you. Using Ubuntu (w/ gnome) 5.04 on 2.6.10-386.. Installed in expert mode (maybe it expected me to know to put myself in that file). Instructions for adding yourself to the sudoers file (if necessary):

# Yes, I know this URL refers to Ubuntu 4.10, but it works just the same for this.

Go here [http://www.myjavaserver.com/~mike001/ubuntu/](http://www.myjavaserver.com/~mike001/ubuntu/) and scroll down to find how to add to the sudoer file. It's really easy.

---

