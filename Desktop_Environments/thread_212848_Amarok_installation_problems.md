---
title: "Amarok installation problems"
date: 2006-07-10
forum: Desktop Environments
---

### Post by tartarian on 2006-07-10
Hey! I downloaded the 1.4.1 tarball of Amarok from their site. I installed all the things it asked me to. I ran ./configure then make then make install under sudo. It didn't output any errors. But, it won't launch at all. Nothing happenes when I click on the icon on K Menu, it wont launch with katapult which gives the error 
"Service '/usr/share/applications/kde/amarok.desktop' is malformatted."
What do I do? 

(Just as an off-hand, can someone give me a list of repositorys that should be/need to be in my sources.list? Because I seem to be getting a lot of "this package could not be found" errors! Thanks!)

---

### Post by Athropos on 2006-07-10
You should not try to compile things by yourself, it's safer and faster to used precompiled packages. To get Amarok 1.4.1, type this in a terminal:

> 
wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
sudo apt-key add kubuntu-packages-jriddell-key.gpg


Then add this line to your /etc/apt/sources/list:

> 
deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main


Then in a terminal:

> 
sudo apt-get update && sudo apt-get upgrade


---

### Post by Rackerz on 2006-07-10
> **Athropos said:**
> You should not try to compile things by yourself, it's safer and faster to used precompiled packages. To get Amarok 1.4.1, type this in a terminal:



Then add this line to your /etc/apt/sources/list:



Then in a terminal:

I suggest to do this also. I never trust building anything from source unless I completely have too and their is no other alternative.

---

