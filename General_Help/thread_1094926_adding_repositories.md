---
title: "adding repositories"
date: 2009-03-13
forum: General Help
---

### Post by nothingspecial on 2009-03-13
How would I modify these lines 

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - 
```

[[COLOR="Red"]To add banshee`s ppa[/COLOR]]("https://edge.launchpad.net/~banshee-team/+archive/ppa") to my sources.lst and add the [[COLOR="Red"]key[/COLOR]]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x4874D3686E80C6B7")

Thanks

---

### Post by nelskurian on 2009-03-13
whats the exact problem?

---

### Post by nothingspecial on 2009-03-13
It`s not a problem, I`m just trying to put all the tweaking and configuring I do after a fresh install into a script that I can just run on all the ubuntu boxes in the house.

I like having the latest banshee. The same applies to gnome-do and wicd but I figured if someone explained how to do it for banshee, I could do the other 2 myself.

Thanks.

---

### Post by sisco311 on 2009-03-13
```

#add the repos
echo -e "deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu intrepid main" | sudo tee -a /etc/apt/sources.list.d/banshee.list
echo -e "deb-src http://ppa.launchpad.net/banshee-team/ppa/ubuntu intrepid main" | sudo tee -a /etc/apt/sources.list.d/banshee.list

#add the key
gpg --keyserver keyserver.ubuntu.com --recv 6E80C6B7
gpg --export --armor 6E80C6B7 | sudo apt-key add -

sudo apt-get update

```

---

### Post by nothingspecial on 2009-03-13
Cheers. Thanks alot!:D

---

### Post by sisco311 on 2009-03-13
oh, you can use [thread=1056099]this[/thread] script to import the keys for all your ppa repos.

---

