---
title: "local repository"
date: 2005-12-20
forum: Desktop Environments
---

### Post by Strannik on 2005-12-20
I downloaded a very huge amount of packages from the Internet onto my pc at work. Now I want to get them all in their original state so that I could burn them on a cd so that I could use them at home. I used the following script to gather the deb packages in one folder: 
#!//bin/sh
dpkg --get-selections | grep -v "deinstall" | awk '{print $1}' | xargs dpkg-repack

I was wondering is it possible to do the following: if i download some other package with apt-get, what changes do I have to do with my script so that it would just syncronize the packages that are in that folder and not rewrite every single package :???:

---

