---
title: "How to install nautilus-elementary on unbutu 11.04"
date: 2011-05-24
forum: Desktop Environments
---

### Post by mjsilverstri on 2011-05-24
Hi,

I have tried to install nautilus-elementary on unbutu 11.04  by doing:

```
sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa
sudo apt-get update
sudo apt-get dist-upgrade
nautilus -q
```

```
$more /etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-natty.list
deb http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu natty mai
n
deb-src http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu natty
 main
```


But after that, I still not get nautilus-elementary. I still get nautilus. I get this after I do a 'About' in Nautilus:
Nautilus 2.32.2.1.

I should get something like 'Nautilus-Elementary or something' right?
Thank you.

---

### Post by Frogs Hair on 2011-05-24
I'm using the same PPA , I would restart the computer . This has happened to others and for some reason nautilus -q didn't work and they had to restart. You placed your code in one box so i hope you entered nautilus -q after the installation was complete.

---

