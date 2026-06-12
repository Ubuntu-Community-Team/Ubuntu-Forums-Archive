---
title: "Why is it so difficult to setup user accounts?"
date: 2008-09-28
forum: Desktop Environments
---

### Post by mashcaster on 2008-09-28
Setting up a single user on an Ubuntu 8.04 machine is simple, however, it is very difficult to setup 2 or more uses on a machine when you don't want any of the other users to be able to see any settings/files of any of the other users.

Why is it so difficult, or have I missed a section which makes this task easy?

The last time I tried this on Ubuntu 7.10, I ended up locking myself out and had to do a clean install.

Has this been improved yet?

---

### Post by olejorgen on 2008-09-29
Agree, I've always found it strange that the default seems to be read access for everyone. Even my uni account had that. chmod o-r /home/user partially works, but iirc you can still do eg. cat /home/user/file.

I guess the real solution is to change the umask. Not sure how you do that though.

---

### Post by aysiu on 2008-09-29
Check out these Brainstorm ideas:
[Idea #6106: Make so other people cant access your home directory ](http://brainstorm.ubuntu.com/idea/6106/)
[Idea #3916: Easy file sharing between local users ](http://brainstorm.ubuntu.com/idea/3916/)

---

