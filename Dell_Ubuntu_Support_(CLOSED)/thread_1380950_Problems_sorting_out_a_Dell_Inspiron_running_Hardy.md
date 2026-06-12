---
title: "Problems sorting out a Dell Inspiron running Hardy Heron"
date: 2010-01-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hamstermoon on 2010-01-14
A student turned up at work today (I work in a college) with a Dell her boyfriend had bought her running Hardy Heron.  On trying to update it says this:

[http://i4.photobucket.com/albums/y116/Hamstermoon/comps/Screenshot-1.png](http://i4.photobucket.com/albums/y116/Hamstermoon/comps/Screenshot-1.png)

Can anyone give me a step by step sort out?

---

### Post by bwallum on 2010-01-14
I can't help you with this but you would get a better response from the 'Absolute Beginners' forum, lots more people there.

---

### Post by tgalati4 on 2010-01-14
Looks like a bad download of a package.  It happens.

In a terminal

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

---

