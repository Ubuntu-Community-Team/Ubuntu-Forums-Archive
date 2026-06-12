---
title: "Apt-get missing libraries with failed MD5 check?"
date: 2005-07-15
forum: Desktop Environments
---

### Post by gust0208 on 2005-07-15
Hello everyone,

I am new user to Ubuntu and fairly new to Linux overall.  I have greatly enjoyed Ubuntu, but have come across a few problems while using apt-get and it not being able to find some libraries since they seem to be failing the MD5 check.  I have gone through the steps on the ubuntu guide to enable the extra repositories and was able to successfully install the updates.  But I am getting this error when adding on new programs, specifically Mplayer and trying to get the Kubuntu KDE environment.  I did a search here for apt-get, but was unable to find any posts with similar problems.

Thanks for the help!

Cheers,
Tom Gustafson

---

### Post by no neck joe on 2005-07-16
Do this

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

Then change anything with "us" 
ie deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main 
to "uk" or "nl" 
ie deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary main

edit: Cheers back at you, Tom

---

### Post by t2kburl on 2005-07-16
I've had a lot of this lately and I have removed the us. from all the lines in sources.list

Now I get ERROR ...Connection Refused when I try to apt-get update   ????????

of course ... it worked this time, when I was trying to get a sample of the error code to post ...

---

### Post by no neck joe on 2005-07-16
[QUOTE=t2kburl]I've had a lot of this lately and I have removed the us. from all the lines in sources.list

Now I get ERROR ...Connection Refused when I try to apt-get update   ????????

of course ... it worked this time, when I was trying to get a sample of the error code to post ...[/QUOTE]


don't just delete the us entries, change them to uk or nl

try using mine.

## Uncomment the following two lines to fetch updated software from the network
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by NeoChaosX on 2005-07-16
Or you could just replace "us" with "ca" or even remove regional part of the address to begin with.

---

### Post by t2kburl on 2005-07-16
ca = Canada?

I had the regionals removed

its too bad they have so many problems with the us.    it seemed a bit quicker to update

at least for me ...  being in the us

---

### Post by t2kburl on 2005-07-16
It happened again ... here is the error message I get

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused)


that is one of many just like it and all of them are from the security repos

edit --- YAAY! 100th post ... pour me another cup  :)

---

### Post by gust0208 on 2005-07-17
[QUOTE=no neck joe]Do this

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

Then change anything with "us" 
ie deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main 
to "uk" or "nl" 
ie deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary main

edit: Cheers back at you, Tom[/QUOTE]

Thanks for the tip, I changed all the US's to UK's and voila!  Everything working great.  I have to give Ubuntu credit, this is a fantastic linux distro, and since I learned about enabling the DMA on my DVD drive, things are going great! :^)

Cheers again and thanks for the help,
Tom

---

