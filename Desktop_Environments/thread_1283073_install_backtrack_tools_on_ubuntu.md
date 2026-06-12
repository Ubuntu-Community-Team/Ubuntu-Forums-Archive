---
title: "install backtrack tools on ubuntu"
date: 2009-10-05
forum: Desktop Environments
---

### Post by m42h31 on 2009-10-05
backtrack 4 rc (base to ubuntu) is possible to download. but i can't install backtrack to my PC because i'm afraid lose my office data inside there (to backup it need too much time).
can i install all backtrack tools in my installed ubuntu?
like apt-get install backtrack maybe :) :lolflag:

thanks..

---

### Post by carnagex420x on 2009-10-05
Backtrack is suite of tools. You can just install the tools you want, or add the repo.


```
wget [http://apt.pearsoncomputing.net/public.gpg](http://apt.pearsoncomputing.net/public.gpg)
sudo apt-key add public.gpg
echo "deb [http://repo.offensive-security.com/dist/bt4](http://repo.offensive-security.com/dist/bt4) binary/">/etc/apt/sources.list
sudo apt-get update
```

You should only use this with Ubuntu 8.10!
apt-get install backtrack still wont work thou.:D

---

### Post by m42h31 on 2009-10-08
> **carnagex420x said:**
> Backtrack is suite of tools. You can just install the tools you want, or add the repo.


```
wget [http://apt.pearsoncomputing.net/public.gpg](http://apt.pearsoncomputing.net/public.gpg)
sudo apt-key add public.gpg
echo "deb [http://repo.offensive-security.com/dist/bt4](http://repo.offensive-security.com/dist/bt4) binary/">/etc/apt/sources.list
sudo apt-get update
```

You should only use this with Ubuntu 8.10!
apt-get install backtrack still wont work thou.:D

very nice info.. thanks bro..

i try this tips but i can download [http://apt.pearsoncomputing.net/public.gpg](http://apt.pearsoncomputing.net/public.gpg) from here..

---

### Post by Roasted on 2009-11-10
> **carnagex420x said:**
> Backtrack is suite of tools. You can just install the tools you want, or add the repo.


```
wget [http://apt.pearsoncomputing.net/public.gpg](http://apt.pearsoncomputing.net/public.gpg)
sudo apt-key add public.gpg
echo "deb [http://repo.offensive-security.com/dist/bt4](http://repo.offensive-security.com/dist/bt4) binary/">/etc/apt/sources.list
sudo apt-get update
```

You should only use this with Ubuntu 8.10!
apt-get install backtrack still wont work thou.:D

Hate to bump this but, why only 8.10? Later release just flat out won't work? 

Is BT3 based on 8.10? Is that why?

---

### Post by sefs on 2009-11-20
Install BackTrack 4 Tools in Ubuntu 9.04

[http://micksmix.wordpress.com/2009/10/28/install-backtrack-4-tools-in-ubuntu/](http://micksmix.wordpress.com/2009/10/28/install-backtrack-4-tools-in-ubuntu/)

---

### Post by Notorious1 on 2009-11-20
Useful info.
 
Thanks

---

### Post by ajmc on 2011-01-25
Is it possible to install BT tools on ubuntu Maverick? My friend wants to use BT on his laptop but he has problems with the ports blocked by default in BT.  I recommended to use ubuntu because I have heard that BT 4 can be merged with ubuntu but I dont know the version.

---

### Post by Slave2Metal on 2011-01-31
> **ajmc said:**
> Is it possible to install BT tools on ubuntu Maverick? My friend wants to use BT on his laptop but he has problems with the ports blocked by default in BT.  I recommended to use ubuntu because I have heard that BT 4 can be merged with ubuntu but I dont know the version.

From the FAQ @ BT

** Why cant I just add the Backtrack repositories to my Ubuntu install or the Ubuntu repositories to my Backtrack install ?**

 We highly recommend against this action because Backtrack tools are  built with many custom features, libraries and kernel. We have no way of  knowing how they will preform on a non Backtrack distribution, plus you  will very quickly break your install.  
Also if you chose to add the ubuntu repositories to your  Backtrack install, you will most certainly break your entire Backtrack  install very quickly. 
We do a lot of testing to ensure that all packages in our repo will work together without causing problems. 
If you decide on this course of action you do so entirely at your  own risk and the backtrack team will not offer any support in any way.

---

### Post by cecilpierce on 2011-05-10
just saw bt 5 on distrowatch.com

---

