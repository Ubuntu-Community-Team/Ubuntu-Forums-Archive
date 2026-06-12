---
title: "Cinnamon: In preferences there is NO Desktop Icon."
date: 2013-05-19
forum: Desktop Environments
---

### Post by artax5005 on 2013-05-19
On Ubuntu 13.04 64 bit, I installed Cinnamon, but inside the system settings there is not the icon named "Desktop" (it should be green). I need these desktop options.

here a screenshot:

[http://i.imgur.com/2y3Ns6V.png?1](http://i.imgur.com/2y3Ns6V.png?1)

Can someone help me to solve this?

Thank you in advance

---

### Post by Frogs Hair on 2013-05-19
Hello and Welcome,
 
In order to get a more complete version of Cinnamon including the Nemo file manager you will likely have to install from a PPA. The repository version is just the basic shell. _Do not_ add the PPA while the repository version is installed on your system and keep in mind PPA' s are use at your own risk. If you have reservations don't install the PPA.

Remove current version```
sudo apt-get remove --purge cinnamon
``` ```
sudo apt-get autoremove
```   


 [https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable](https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable)

```
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
``````
sudo apt-get update
``````
 sudo apt-get install cinnamon-stable
```

---

