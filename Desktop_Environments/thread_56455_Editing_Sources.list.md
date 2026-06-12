---
title: "Editing Sources.list"
date: 2005-08-12
forum: Desktop Environments
---

### Post by pencortod on 2005-08-12
Hey All,
 I am a real n00B at Linux and after 18 years of MS flavors I am attempting to do Ubuntu  to get my feet wet. I have it all installed, functional and I am finding my way around OK however I am attempting to mod the sources list to find and install Ethereal and I can open the file in Gedit but I do not own it logged on as my new user I created and I cannot for the life of me figure out (1) if I should edit as root or (2) if I should change file permissions on the file (3) or the Subdir it resides in. can you point me in the right direction or finger a list I can browse?

Thanks

---

### Post by heimo on 2005-08-12
You should edit it with root privileges, use
 ```
sudo gedit /etc/apt/sources.list

``` 

ethereal is in universe (section of Ubuntu repositories):
[http://packages.ubuntu.com/hoary/net/ethereal](http://packages.ubuntu.com/hoary/net/ethereal)

So you need to add universe, you can do it in Synaptic, too:
[https://wiki.ubuntu.com/UniversePackages](https://wiki.ubuntu.com/UniversePackages)

Unofficial Ubuntuguide has some other instructions:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

