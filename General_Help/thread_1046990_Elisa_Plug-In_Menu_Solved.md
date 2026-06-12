---
title: "Elisa Plug-In Menu Solved"
date: 2009-01-22
forum: General Help
---

### Post by chiefchief on 2009-01-22
Just wanted to post a fix I found with Elisa.

If this is a duplicate posting, I apologize, I searched the forums for the solution (and a lot of the internet) but could find nothing on the topic.

Problem:  Elisa installed by default through apt-get will not access the plug-in menu and no plug-ins will work (the big gear, what I initially thought was a 'configuration' menu).

Solution:  Provided by Elisa [wiki]("http://elisa.fluendo.com/wiki/Distribution/LinuxPackages") (although no acknowledgement of bug)

Add this line to your sources.  System > Administration > Software Sources > Third-Party Software:
```
deb http://ppa.launchpad.net/elisa-developers/ubuntu intrepid main
```
Reload your sources
```
sudo apt-get update
```
Install Elisa
```
sudo apt-get install elisa
```
It will update a package and install the full plugin set good/bad/ugly, while the default sources only install good/bad.  Also, mine did not work until I ran system update and upgraded another python package.

Hope this helps somebody =)

---

### Post by xboxSlayer on 2009-02-08
Thanks! This was exactly what I was looking for. Plugins work fine now.

---

### Post by taaheel on 2009-04-20
hi.. thanks alot am doing it right now .. I was looking for this for a long time .. thanks again !!

---

