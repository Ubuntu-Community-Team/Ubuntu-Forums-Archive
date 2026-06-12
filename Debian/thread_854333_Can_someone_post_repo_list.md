---
title: "Can someone post repo list?"
date: 2008-07-09
forum: Debian
---

### Post by L815 on 2008-07-09
I installed from debian CD with no internet during install, and when I went to check the sources list, only the cd & security for lenny were listed.

I've been searching for about an hour and have not found a sound solution.

Can someone post their repo list for:
lenny
sid
multimedia 

I want to use sid and the only way is updating through lenny correct?
I want up-to-date apps, etc... I don't mind that it might not be stable :P

Anyway, it would be much appreciated!

---

### Post by benuski on 2008-07-09
[www.debian.org/mirrors](www.debian.org/mirrors) is the list of all worldwide debian mirrors.

deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) sid main
deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) lenny main

If you don't live in the States, replace us with the two letter code of your country.

I forget the debian multimedia one, but instructions for how to do it are on their website, which is just debian-multimedia.org.

If you already have lenny installed, I think an aptitude update and aptitude dist-upgrade should get you into a sid system.  Actually, that should just work if you installed etch too.

---

### Post by L815 on 2008-07-09
Thanks for replying so quick. :popcorn:

---

