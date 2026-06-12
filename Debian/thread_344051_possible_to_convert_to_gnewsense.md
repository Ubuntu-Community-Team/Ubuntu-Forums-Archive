---
title: "possible to convert to gnewsense?"
date: 2007-01-22
forum: Debian
---

### Post by deanlinkous on 2007-01-22
Yes it is possible!

No need to repent....just convert ;)

Just wanted to let everyone know it is possible since gnewsense is basically dapper. All you need to do is change your sources.list to gnewsense sources and install the gnewsense kernel and artwork stuff. Of course if you wanted to you could keep the ubuntu artwork if you like including the ubuntu usplash. 

You could even have both kernels installed and select which you want on the grub boot screen. So you can give gnewsense a try-out and if your hardware is not supportted then you can go back to the Ubuntu kernel. Even better you could re-evaluate your hardware choices and become free-compatible! ;)

If anyone needs exact steps just post and I will outline it a bit better.

---

### Post by celsofaf on 2007-01-22
If someone wants to do it, remember also to take out from your system proprietary stuff you might have installed, like Skype, mp3 support and such. Good luck!

---

### Post by deanlinkous on 2007-01-22
> **celsofaf said:**
> If someone wants to do it, remember also to take out from your system proprietary stuff you might have installed, like Skype, mp3 support and such. Good luck!

:confused:

---

### Post by picpak on 2007-01-22
There's nothing saying you should remove it, but it'd be hypocritical to run a distro like gNewSense with proprietary programs.

You can see how much proprietary stuff you have by running vrms (it's in the repos).

---

### Post by deanlinkous on 2007-01-22
Well at least with choosing to run non-free software you actually had a choice.... :D

---

### Post by deanlinkous on 2007-01-22
Here is a script I use to convert dapper to gnewsense. This is just provided as a example of how to convert to gnewsense. I would not suggest using this since it may do things that you do not want done. 

#move my original sources
mv /etc/apt/sources.list /etc/apt/sources.list.BACKUP

#grab my gpg stuff saved from my gnewsense install
mkdir /etc/apt/OLDgpg
mv /etc/apt/*.gpg /etc/apt/OLDgpg
cp ./gpgStuff/*.gpg /etc/apt/

#create a sources.list
touch /etc/apt/sources.list

#add the correct lines to the sources.list
echo deb [http://us.archive.gnewsense.org/gnewsense/](http://us.archive.gnewsense.org/gnewsense/) deltad main universe >> /etc/apt/sources.list
echo deb-src [http://us.archive.gnewsense.org/gnewsense/](http://us.archive.gnewsense.org/gnewsense/) deltad main universe >> /etc/apt/sources.list
echo deb [http://us.security.gnewsense.org/gnewsense/](http://us.security.gnewsense.org/gnewsense/) deltad-security main universe >> /etc/apt/sources.list
echo deb-src [http://us.security.gnewsense.org/gnewsense/](http://us.security.gnewsense.org/gnewsense/) deltad-security main universe >> /etc/apt/sources.list
echo deb [http://us.security.gnewsense.org/gnewsense/](http://us.security.gnewsense.org/gnewsense/) deltad-updates main universe >> /etc/apt/sources.list
echo deb-src [http://us.security.gnewsense.org/gnewsense/](http://us.security.gnewsense.org/gnewsense/) deltad-updates main universe >> /etc/apt/sources.list
echo deb [http://us.security.gnewsense.org/gnewsense/](http://us.security.gnewsense.org/gnewsense/) deltad-backports main universe >> /etc/apt/sources.list
echo deb-src [http://us.security.gnewsense.org/gnewsense/](http://us.security.gnewsense.org/gnewsense/) deltad-backports main universe >> /etc/apt/sources.list

#update apt
apt-get update
 
#dist upgrade should pull in kernel and other stuff
apt-get dist-upgrade --assume-yes --force-yes

#remove the old kernel and modules and stuff
apt-get remove --assume-yes --force-yes --purge linux-restricted-* linux-image-2.6.15-26-386 nvidia-kernel-common

#remove usplash and artwork and so forth
apt-get remove --assume-yes --force-yes --purge usplash ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-minimal ubuntu-standard

#install artwork and some stuff
apt-get install --assume-yes dialog gnewsense-artwork gnewsense-desktop gnewsense-minimal gnewsense-standard

---

### Post by Dr. C on 2007-01-22
> **picpak said:**
> There's nothing saying you should remove it, but it'd be hypocritical to run a distro like gNewSense with proprietary programs.

You can see how much proprietary stuff you have by running vrms (it's in the repos).

vrms will find proprietary stuff installed via synaptic apt etc. but it will not find proprietary stuff installed by running an installer. For example Vmware (and any virtualized proprietary OS), Google earth etc. It should not be used to give a system a clean bill of health, that is not what it was designed to do.

---

### Post by deanlinkous on 2007-01-22
vrms is not 100% accurate in regard to installed packages either - probably needs some updates but it is a good start :)

---

### Post by steven8 on 2007-01-22
I said it before, and I"ll say it again, gNewSense is just fine.  It worked with all of my hardware and I have a USB cable modem that almost NO distros want to work with.  I would recommend gNewSense to anyone!

---

### Post by deanlinkous on 2007-01-23
:)
I have a omnibook 6000 with a orinoco wireless card, a recently built system with a MSI board and another recently built system with a Mercury board and a old p2 system and they are all happy with gNewSense as was the dell dimension 3000 that I just got rid of!

Dapper is a d&mn good release....

---

### Post by steven8 on 2007-01-23
Yes, Dapper is rock solid.  So, gNewSense, made up of totally 'free as in freedom' components, is built on one of the best distro releases ever.

You can't go wrong!

---

### Post by RAV TUX on 2007-01-23
moving to the Debian (and derivatives) forum

---

### Post by deanlinkous on 2007-01-24
Split my script into parts to make it a bit safer(?)
Part 1 should just install the gnewsense kernel and some other stuff I believe. Then you should be able to reboot and it will use the gnewsense kernel.
Part 2 will remove the ubuntu kernel, lrm, ubuntu artwork, and install the gnewsense artwork.

At your own risk of course.....

[http://communia.nrvitsquad.com/gNewConvertDap.tar.gz](http://communia.nrvitsquad.com/gNewConvertDap.tar.gz)

---

### Post by steven8 on 2007-01-24
Oh heck, just back up your stuff, dowload the iso, and do a fresh install.  It's worth it!

---

### Post by deanlinkous on 2007-01-24
Good point! I install dapper because I can do a server install and then upgrade that to a 'lite' gnewsense. Also I can install dapper using a external cd drive on my laptop(no-cd)!

---

### Post by deanlinkous on 2007-02-10
(bump)
just seemed like a good time for bumping this thread....

---

