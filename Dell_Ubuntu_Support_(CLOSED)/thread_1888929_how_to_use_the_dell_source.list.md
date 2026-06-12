---
title: "how to use the dell source.list ?"
date: 2011-11-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kytexzy on 2011-11-30
Hi, everyone:
    I use Dell vostro 1450D-276, and I installed Ubuntu 11.10. I want to add the source:
[http://dell.archive.canonical.com/dists/oneiric-dell/public/](http://dell.archive.canonical.com/dists/oneiric-dell/public/)
to my /etc/apt/source.list, and I edit my source.list
deb [http://dell.archive.canonical.com/ubuntu](http://dell.archive.canonical.com/ubuntu) oneiric-dell public
But when I run:
sudo apt-get update
I get errors:
W: [http://dell.archive.canonical.com/ubuntu/dists/oneiric-dell/public/binary-i386/Packages](http://dell.archive.canonical.com/ubuntu/dists/oneiric-dell/public/binary-i386/Packages)  404  Not Found

I want to add the source of [http://dell.archive.canonical.com](http://dell.archive.canonical.com) to my source.list. Who can tell me how to add it to my source list.

---

### Post by jerrrys on 2011-12-01
it sounds like you have your sources set up right.  open up your "software sources" use the "other" option to find best server.  I think that will clear a 404

---

