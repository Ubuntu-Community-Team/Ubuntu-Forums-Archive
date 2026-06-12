---
title: "How to run latest version of Empathy in Jaunty?"
date: 2009-06-21
forum: General Help
---

### Post by golusweet on 2009-06-21
New version supports adium themes,and few others.

Can anyone tell me how to grab the latest version of Empathy,and change to adium theme.:D

---

### Post by bluenova on 2009-06-22
First add the public key from the developers: 
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FA3A1271
```
Next add the following repositories depending upon your Ubuntu version to /etc/apt/sources.lst or graphically in System->Administration->Synaptic Package Manager->Settings->Repositories: 
For Jaunty(9.04) Users 
```
deb http://ppa.launchpad.net/telepathy/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/telepathy/ppa/ubuntu jaunty main
```

[http://live.gnome.org/Empathy/Install](http://live.gnome.org/Empathy/Install)

---

### Post by madmax.santana on 2009-11-08
Just to let you know that just:
> sudo apt-get install empathy
Worked perfectly for me. I didn't have to import key and add that repository.

---

