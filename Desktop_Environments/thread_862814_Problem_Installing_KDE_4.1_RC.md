---
title: "Problem Installing KDE 4.1 RC"
date: 2008-07-17
forum: Desktop Environments
---

### Post by Brando569 on 2008-07-17
when i try to install the kubuntu-desktop-kde4 package i get this error when using apt-get:
E: /var/cache/apt/archives/kde-window-manager_4%3a4.0.98-0ubuntu1~hardy1~ppa2_amd64.deb: trying to overwrite `/usr/lib/kde4/share/doc/kde4/HTML/en/kcontrol/kwindecoration/index.docbook', which is also in package kdebase-runtime-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde-window-manager_4%3a4.0.98-0ubuntu1~hardy1~ppa2_amd64.deb


and this error when using synaptic:

E: /var/cache/apt/archives/kde-window-manager_4%3a4.0.98-0ubuntu1~hardy1~ppa2_amd64.deb: trying to overwrite `/usr/lib/kde4/share/doc/kde4/HTML/en/kcontrol/kwindecoration/index.docbook', which is also in package kdebase-runtime-data

---

### Post by apswartz on 2008-07-21
I was wondering if you ever got your problem fixed. I was having a similar problem and I ended up having to manually remove, install and reinstall various packages to get things working again.

A word of advice: if you start messing around like that be sure you have another desktop environment installed in case you need to log in with it. I keep xfce installed for that very reason. ;-)

---

### Post by Brando569 on 2008-07-21
i have kde 3.5.9 installed as my default WM i think i might just remove the RC and wait until the final comes out its only going to be about 6 days right?? if i ever screw anything up really bad im relatively adept at using the console so i could either fix it using aptitude or a live cd, if all else fails copy the files you changed, save stuff and reinstall it :D

---

### Post by rebegin on 2008-07-30
hey,
i've just tried to install the final KDE 4.1 and had the same problem. but i found the solution:
```

sudo gedit /var/lib/dpkg/info/kdebase-runtime-data.list

```
or if you're using xfce:
```

sudo mousepad /var/lib/dpkg/info/kdebase-runtime-data.list

```

and delete all lines begining with /usr/lib/kde4/share/doc
save and close. after that 

```

sudo apt-get -f install
sudo apt-get update && sudo apt-get upgrade

```


taken from here:
[http://news.softpedia.com/news/How-To-Install-KDE-4-1-On-Ubuntu-8-04-91034.shtml](http://news.softpedia.com/news/How-To-Install-KDE-4-1-On-Ubuntu-8-04-91034.shtml)

i hope it helps someone.

---

### Post by Brando569 on 2008-08-02
thanks but i think im still going to stay away from kde 4.1 for awhile its still not as easy to use as kde 3.5.x is.

---

