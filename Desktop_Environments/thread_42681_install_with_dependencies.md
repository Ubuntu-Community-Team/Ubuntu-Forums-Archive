---
title: "install with dependencies"
date: 2005-06-19
forum: Desktop Environments
---

### Post by jrev on 2005-06-19
Hi all,

How do you install with dependencies a lonely package which was missing on the installation DVD or CD ?
I downloaded the "gnome-ppp" necessary for my dialup connection and I don't know the command to install it with Synaptic

thanks for your help O:)

---

### Post by TripHammer on 2005-06-19
that packages (gnome-ppp) is in the universe repository, no need to download it and install it by itself.  Change your /etc/atp/sources.list to include the 'universe' and 'multiverse' respositories:

(assuming hoary)

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe multiverse

then:
sudo apt-get update && sudo apt-get install gnome-ppp

/Cheers

---

### Post by jrev on 2005-06-22
Thanks 
but I must first get a steady internet connection
I had one but think it has been marred by my trial to share this internet connexion.
We really need a tuto on the way to share an internet connection ...
 would make one if I can get out of this problem.

My first job should be :
1 delete the internet partitionning 
2 configure a steady internet connection
3 configure the web sources 

any idea about point one ? :-|

---

