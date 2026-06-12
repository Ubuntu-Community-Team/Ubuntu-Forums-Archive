---
title: "divx-&gt;dvd? tovid install?"
date: 2005-12-10
forum: Desktop Environments
---

### Post by salsaseb on 2005-12-10
I'm a linux newbie, trying to figure out how to convert divx files to dvd.
another post on this forum suggested tovid, a suite of scripts that can handle that.
however, I'm running into headaches trying to figure out all the dependencies...

could anyone suggest a step-by-step guide to getting tovid and all its depencencies to work on ubuntu 5.10?

or any other way to simply convert one or several divx files into one dvd (I don't need elaborate menus...)

---

### Post by kairu0 on 2005-12-10
I *just* (literally 15 minutes ago) burned my first video DVD in Ubuntu using the tovid scripts. I tried a whole bunch of software and they were the easiest.

First, add this to your /etc/apt/sources.list

```
deb http://packages.kirya.net unstable main contrib non-free
deb-src http://packages.kirya.net unstable main contrib non-free
```

Then, run ```
sudo apt-get update
```

Use Synaptic to install tovid. Now follow this howto to burn your DVD:

```
http://tovid.sourceforge.net/howto.html
```

---

### Post by salsaseb on 2005-12-10
great!
I tried that, but ran into some dependency issues with mplayer, mencoder, mjpegtools and transcode, which are not available.
Do you have any other repositories enabled in your sources.list?

Thanks for your help!

---

### Post by kairu0 on 2005-12-10
Mplayer, mencoder, mjpegtools, and transcode should all be available in the universe + multiverse repositories.

Here is my sources.list

```

deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
#deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

#OpenOffice

deb http://people.ubuntu.com/~doko/OOo2 ./

# Java, Realplayer, Skype...

deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf breezy free non-free

```

---

### Post by jtpratt on 2006-03-16
well, if you're looking for a guide, I just wrote (and updated) one for Ubuntu 5.10 video conversion and Tovid type stuff....hope it helps:

[http://smorgasbord.net/convert_video_linux]("http://smorgasbord.net/convert_video_linux")

---

