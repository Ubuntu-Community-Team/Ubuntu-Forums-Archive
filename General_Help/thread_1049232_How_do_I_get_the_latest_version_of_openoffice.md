---
title: "How do I get the latest version of openoffice?"
date: 2009-01-24
forum: General Help
---

### Post by Fzang on 2009-01-24
Using 8.10, I only have openoffice 2.4 in my repos it seems, while there's a version 3 out. Why am I not getting version 3 as an update or anything?

I tried installing version 3 by downloading from openoffice.org but I got a lot of random .deb files everywhere which didn't want to install... and stuff like that...

---

### Post by lovelyvik293 on 2009-01-24
Installing OpenOffice 3.0 in Ubuntu 8.10

Take a terminal and run:
```


    echo 'deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main' >> /etc/apt/sources.list.d/openoffice.sources.list && sudo apt-get update

```

---

### Post by taurus on 2009-01-24
> **lovelyvik293 said:**
> Installing OpenOffice 3.0 in Ubuntu 8.10

Take a terminal and run:
```


    echo 'deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main' >> /etc/apt/sources.list.d/openoffice.sources.list && sudo apt-get update

```

You know that command (the first part) would not work because it will complain about permission.

---

### Post by lovelyvik293 on 2009-01-24
@taurus
sorry but m using the root so no permission problem.

---

### Post by Fzang on 2009-01-24
Thank you

And don't worry, I can overcome writing sudo

---

### Post by taurus on 2009-01-24
> **lovelyvik293 said:**
> @taurus
sorry but m using the root so no permission problem.

Because you know how to create a password for root and log in as root but others, especially the newbies, don't.

And if you log in as root, why do you even have the sudo in the command (second part) anyway?

---

### Post by HarmonicaGoldfish on 2009-01-24
I recently followed the instructions here and now have oo3 installed and working well.


[Install OpenOffice.org 3.0 on Ubuntu]("http://www.tectonic.co.za/?p=3363")

---

### Post by MikeBrown on 2009-01-24
I've noticed that you get **much** better download speeds if you use a P2P  or Torrent program like transmission to get the latest install. The official OpenOffice.org torrent link is here [http://distribution.openoffice.org/p2p/](http://distribution.openoffice.org/p2p/) 

You might have to check back at the site sometimes to see if there are updates, which is the only downside. 

I know I saw a method of automating the Torrent download of any updated version, and if I can re-find that article, I will post it here. 

***EDIT: Found one article on speeding up download speeds: [http://ubuntu.wordpress.com/2005/10/14/22x-faster-upgrade/](http://ubuntu.wordpress.com/2005/10/14/22x-faster-upgrade/)

Hope this helps!

---

