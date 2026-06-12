---
title: "Problem installing opera"
date: 2006-06-10
forum: Desktop Environments
---

### Post by blanc11 on 2006-06-10
I get this message when installing opera through synaptic

```
opera:
 Depends: xlib6g (>=3.3.6) but it is not installable or
 	xlibs  but it is not installable
``` what does it mean?

---

### Post by shuttleworthwannabe on 2006-06-10
For some reason this is not new. It has happened to me so many time, quite frustrating I must say. Theree is a Wiki documentation on this which may be worth visiting [https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser). Otherwise, try this in Terminal

$ sudo apt-get -f install

if this does not correct the dependencies, it will remove the broken app and remove the half installed Opera.

Not really a solution, but I would try the new Opera 9 beta (it is fairly stable and works great). Check the HOWTO section in these forums for a good HOWTO on installing Opera 9beta.
[http://www.ubuntuforums.org/showthread.php?t=177449](http://www.ubuntuforums.org/showthread.php?t=177449)
Good luck.

---

### Post by effoff on 2006-06-10
You need to install xlibs. Get it here
[http://www.artfiles.org/ubuntu.com/archive/pool/main/x/xorg/](http://www.artfiles.org/ubuntu.com/archive/pool/main/x/xorg/)
Get the xlibs_6.8.2-77.1_all.deb
Download it then do a **sudo dpkg -i /folder/where/xlibs_6.8.2-77.1_all.deb**

Also installing lesstif2 (synaptic) is a good idea so that all Opera plugins will work well.

---

### Post by cjm5229 on 2006-06-10
or use Automatix, Arnieboy has really dialed it in. It was good in  Breezy but the latest version  is really awesome.

---

### Post by blanc11 on 2006-06-10
Thanks for all the responses! Now I am having trouble installing flash. Where do I install it?

---

### Post by shuttleworthwannabe on 2006-06-10
It should be in the repo's: [https://wiki.ubuntu.com/RestrictedFormats#head-29ce85c5f75a6380ed26f1e828c343e54074d6e0](https://wiki.ubuntu.com/RestrictedFormats#head-29ce85c5f75a6380ed26f1e828c343e54074d6e0) for further instructions.

Also I have noticed that mutiverse is not responding of late. Wait and retry later.

---

### Post by martinbriscoe on 2006-08-29
I have a different problem installing opera 9.

I have installed it ok using the recent guidelines ([www.ubuntu.com/news/opera9?highlight=%28opera%29](www.ubuntu.com/news/opera9?highlight=%28opera%29))

Its icon appears in the program menu and on the bottom panel, but when I click on the icon - I can hear the hdd turn over for a few secs but the program doesnt launch. Any ideas?

Martin
ubuntu 6.06

---

