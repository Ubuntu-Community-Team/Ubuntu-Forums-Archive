---
title: "Kubuntu login scren color"
date: 2009-06-03
forum: Desktop Environments
---

### Post by joeldic on 2009-06-03
I am running ubuntu, (Go Gnome!), but wanted to check out kde, so I installed the kubuntu-desktop in synaptic. Then, for the log in screen, I was getting the kubuntu login screen and progress bar when starting up. Also, my /etc/rc3.d included both S30gdm and S30kdm. I was able to solve it by doing the following.

1. System -> Administration -> Login Window. I selected the Human theme, and changed the Background color to the ubuntu orange/brown
2. System -> Administration -> Services. I un-ticked the box for kdm, becuase I had both selected.

There are two things though that I can't revert.

1. After I'm logged in and befor the ubuntu background has a chance to load, the screen is still the kubuntu blue/grey.
2. Although my /etc/rc3.d/ scripts now included only the S30gdm script, some other rc.d's, namely, rc4.d and rc5.d still included both S30gdm and S30kdm scripts racing each other.

How to I fix this?

---

