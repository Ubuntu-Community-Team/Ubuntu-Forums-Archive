---
title: "default bash settings for all users"
date: 2009-03-20
forum: General Help
---

### Post by KayakJim on 2009-03-20
I have tried searching both these forums as well as with Google in general and have not been able to find an answer to my question. My guess is that I am using the wrong search terms.

I have a server running Ubuntu 8.04 Hardy and would like to setup default settings for the bash shell for all users.

If I understand things correctly, when I create a new user a copy of the /etc/skel/.bashrc file is placed in their home folder.

If I modify the /etc/skel/.bashrc file, any existing users do not receive the updates.

Is there another file that I can edit that is read each time a shell is started for every user?

---

### Post by taurus on 2009-03-20
/etc/bash.bashrc

---

