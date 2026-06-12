---
title: "How To compile FTP"
date: 2006-09-20
forum: Desktop Environments
---

### Post by rianquinn on 2006-09-20
I have an interesting question for all of you Linux Experts. I need to be able to modify the actual code for ftp. Where are the sources for ftp, and how do I get them? Also, once I have them how should I go about compiling them?

Thanks,
Rian

---

### Post by andypaxo on 2006-09-20
You can get hold of the sources through apt (Make sure you enable the source repositories - the Ubuntu guide will tell you how)

The following command will download the sources, you should create a new directory to run this in:
apt-get source ftp

You will then have a folder in your current directory called netkit-ftp-0.17 (as well as a bunch of other files)

You can compile the program in the usual manner:
./configure
make
(Then run 'make install' as root if you wish to install)

If ./configure gives you any errors along the lines of 'This package needs xxx to run', then install xxx-dev from apt

Hope this helps!

---

### Post by rianquinn on 2006-09-20
(SOLUTION: Post #2)

Awesome!

Thats exactly what I needed. I had to install libnurses5-dev but after that everything when smoothly. Thanks alot.

Rian

---

