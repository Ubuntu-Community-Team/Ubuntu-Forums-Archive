---
title: "installing compizconfig-settings-manager"
date: 2008-02-29
forum: Desktop Effects &amp; Customization
---

### Post by binil on 2008-02-29
Hi guys, I am new to this site.I want to install compizconfig-settings-manager
into my ubuntu, but my synaptic package manager does'nt list it. Also I have download
compizconfig-settings-manager from the ubuntu download site and stored into a desktop
folder. Can I install this package from that folder ?

I dont have an internet connection in my home i.e in my ubuntu system so pls help me

---

### Post by Therion on 2008-02-29
1. Open a terminal window.

2. Execute the following command:
```
sudo aptitude install compizconfig-settings-manager
```

---

### Post by santiagoward2000 on 2008-02-29
> **binil said:**
> Hi guys, I am new to this site.I want to install compizconfig-settings-manager
into my ubuntu, but my synaptic package manager does'nt list it. Also I have download
compizconfig-settings-manager from the ubuntu download site and stored into a desktop
folder. Can I install this package from that folder ?

I dont have an internet connection in my home i.e in my ubuntu system so pls help me

Hi!
First, go to **System/Software Sources** and enable the Universe and Multiverse boxes. Then, go back to Synaptic and look for it again.
Cheers!

---

### Post by Nythain on 2008-02-29
> **binil said:**
> 
I dont have an internet connection in my home i.e in my ubuntu system so pls help me
people really dont know how to read now a days... sudo aptitude install compizconfig-settings-manager isnt gonna do much good, nor is enabling repos he cant connect to...

you can however, go to
[http://packages.ubuntu.com](http://packages.ubuntu.com)
search for compizconfig-settings-manager
and download the package for it, and any of its dependancies onto a portable drive or burn to cd from a computer with the internet (im assuming you have access to the internet SOMEWHERE since you mentioned you did download the package at some point in time)
then just install with
sudo dpkg -i <package name>

hopefully that made sense and helps you out a bit... if you do in fact have internet then the above mentioned recomendations will work too

---

### Post by luke1026 on 2008-02-29
> **santiagoward2000 said:**
> Hi!
First, go to **System/Software Sources** and enable the Universe and Multiverse boxes. Then, go back to Synaptic and look for it again.
Cheers!

Cheers for that... everything now works :D

---

### Post by santiagoward2000 on 2008-02-29
> **luke1026 said:**
> Cheers for that... everything now works :D

\\:D/ I'm glad I could help you!
Although I'm not sure how that did it if you have no internet :confused:

> **Nythain said:**
> people really dont know how to read now a days... sudo aptitude install compizconfig-settings-manager isnt gonna do much good, nor is enabling repos he cant connect to...
:oops: Sorry about that. Honestly, as it was one line lower, I past through it thinking it was a signature or something. I'll try to pay more attention next time!

---

### Post by skyv.ism on 2008-06-01
[SIZE="3"][COLOR="Blue"]When I enable system->prferences->appearance->visual effects->extra effect,I lost the garbage window appearance and lost the minimiation/maximization/x options from the window.

what should I do to get both the extra effect without garbage window appearance.[/COLOR][/SIZE]

---

### Post by ynnorj on 2008-06-09
> **Nythain said:**
> 

you can however, go to
[http://packages.ubuntu.com](http://packages.ubuntu.com)
search for compizconfig-settings-manager
and download the package for it, and any of its dependancies onto a portable drive or burn to cd from a computer with the internet (im assuming you have access to the internet SOMEWHERE since you mentioned you did download the package at some point in time)
then just install with
sudo dpkg -i <package name>


I have just installed ubuntu on my pc last week. I also do not have an Internet connection at home. So I tried your suggestion. But there are just a lot of dependencies to download. Is there anything easier than manually downloading all its dependencies? Thanks!

---

