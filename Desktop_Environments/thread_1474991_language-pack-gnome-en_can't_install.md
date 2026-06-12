---
title: "language-pack-gnome-en can't install"
date: 2010-05-06
forum: Desktop Environments
---

### Post by cybernet on 2010-05-06
Installing package(s) with command apt-get -y install language-pack-gnome-en ..

Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  language-pack-gnome-en: Depends: language-pack-gnome-en-base (>= 1:10.04+20100422) but 1:10.04+20100421 is to be installed
                          Depends: language-pack-en-base (>= 1:10.04+20100422) but 1:10.04+20100421 is to be installed
E: Broken packages

.. install failed!

please help :)

ubuntu version is 10.04

---

### Post by djsutton on 2010-05-06
I have the same error.  check the bug report here

[https://bugs.launchpad.net/ubuntu/+source/language-pack-gnome-en/+bug/576624](https://bugs.launchpad.net/ubuntu/+source/language-pack-gnome-en/+bug/576624)

---

### Post by mexicanseaf00d on 2010-07-17
sorry for warming this thread up, but i just got the same errors with the -de language packs

it was my own fault i guess, because i tried to reinstall the de packs to get rid of the the greyed out language pack updates in updatemanager

that obviously didnt help and now i'm stuck with the same 'broken package' + dependency loop errors like the OP

:o

---

### Post by Bluebearbevis on 2010-07-17
Help,

I just did the exact same thing that mexicanseaf00d did and bingo, this dependency issue.  I followed the bug link, but the posts are old and say the problem was solved by updates, it's now July and I am not being able to do that.  ?!?

Thank in advance for any  solutions, suggestions, or simply sympathy,

Richard

---

