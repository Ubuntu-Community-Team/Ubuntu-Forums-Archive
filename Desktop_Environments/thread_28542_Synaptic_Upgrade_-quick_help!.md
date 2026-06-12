---
title: "Synaptic Upgrade? -quick help!"
date: 2005-04-20
forum: Desktop Environments
---

### Post by Alex4R on 2005-04-20
I ran the 'sudo apt-get upgrade' command in the terminal, and I thought it was supposed to upgrade all of my installed applications? It didnt seem to upgrade anything, Firefox was still 0.9.x and GAIM was still 1.0.0. I ran update first. Does upgrade not do what I am thinking it does? I need to upgrade pppd to 2.4.3, because tonight is my only night on cable, I need to get everything done that way I can connect on dial-up hopefully when I get home.

Thanks!

---

### Post by Leif on 2005-04-20
Packages in a stable release, which warty certainly is, won't get upgraded in the sense you're thinking, they will mainly get security updates and bugfixes. You can see if the backports project has the upgrades you want (backports.ubuntuforums.org), or you can upgrade the whole lot to hoary.

---

### Post by Alex4R on 2005-04-20
Thanks for the quick reply, to upgrade to hoary would I just update all of my repositories to hoary ones, and then run an 'apt-get dist-uprade'?

---

### Post by Leif on 2005-04-20
Basically, yes, with an apt-get update in between. Good luck !

---

### Post by Alex4R on 2005-04-20
I'm using the following repositories:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe

Are there any others I should use? Thanks!

---

### Post by Leif on 2005-04-20
I have :

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

these are the basic ones. I also have backports for upgrades :

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

---

### Post by Alex4R on 2005-04-20
That was easy enough, it was all updated successfully!

Thanks for your help! :D

---

