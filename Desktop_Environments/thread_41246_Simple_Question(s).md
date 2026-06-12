---
title: "Simple Question(s)"
date: 2005-06-12
forum: Desktop Environments
---

### Post by Krogen on 2005-06-12
1) I did a server installation (base installation).

2) Now I'm trying to "apt-get install kubuntu-desktop". I get a failed to fetch error. Couple files don't download. [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) is down? I guess..

3) Trying to install gedit to remove that line from the sources.list. "apt-get install gedit". Ok.

4) cd /etc/apt/     gedit sources.list

Got an error saying: Gtk-Warning - Cannot open display:




One more thing. What should I replace those not-working links with? 

Thanks.

---

### Post by SGC on 2005-06-12
I'm not sure, but isn't the base instalation does not have the x server(or whatever it called), if that true you will not be able to open gedit or any application with a gui.

Try to use nano , it is an easy to use comand line text editor

nano /etc/apt/apt/sources.list
once you open the file change all refrence to [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) into [http://archive.ubuntu.com/](http://archive.ubuntu.com/)

save the file (ctrl+O with nano) and apt-get update

---

### Post by Krogen on 2005-06-12
Thanks. I did so and everything was smooth until I saw the "configuring xserver-xorg" screen. MY KEYBOARD FROZE!!! And it was working a second ago!

I guess the only thing I can do is reboot?

---

### Post by Martin Witte on 2005-06-12
I just installed kubuntu, coming from a Hoary installation. My /etc/apt/sources.list is below. My understanding is that to do the installation of the kubuntu desktop you need to have a full ubuntu hoary installation (or a kubuntu cd), so you need xorg and so already installed.

martin@ubuntu:~$ cat /etc/apt/sources.list


deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
martin@ubuntu:~$

---

### Post by Krogen on 2005-06-12
Yes... Yes... Thanks. All I did was remove the "us" from each one of the links and everything went on smoothly.

Right now I have a different problem which I got in couple other linuxes. FREEZING.

---

### Post by Burgundavia on 2005-06-12
us.archive is current seriously messed. The issue is being sorted out.

Corey

---

