---
title: "Adept Manager crashing in Kubuntu?"
date: 2007-10-23
forum: Desktop Environments
---

### Post by handy on 2007-10-23
I've just done a fresh install of Kubuntu 7.10, set up the repo's in Adept Manager, then installed the nVidia restricted driver, then went for the kubuntu-restricted-extras metapackage & I get crash after crash, it will not work?

Anyone having the same problem or any understanding on why?

---

### Post by ~psych~ on 2007-12-27
I'm having a similar error !!
Everytime I try to open adept manager, it gives me the following:
Database Locked. Another process is using the packaging system database. 
And it asks if I want to resolve. If i click yes Adept manager closes and gives me a crash error.. 
Some help is much appreciated !!

---

### Post by AlanR8 on 2007-12-27
Had the same issue. I've noticed on a fresh install of 7.10, the updates do not come down clean. In Adept it fails.

So do sudo apt-get update

The update will start but come up with an error message that basically tells you what to do. Don't quote me but it's something like dpkage -a.

When I've done this a message comes up about overwriting a file, I choose NOT to overwrite and all is well after that

---

### Post by ~psych~ on 2007-12-28
Yes man all is well now :D Even adept is not crashing :D. Thanks !!

---

### Post by AlanR8 on 2007-12-28
You're welcome

---

