---
title: "Apt-get dependencies trouble"
date: 2005-05-11
forum: Desktop Environments
---

### Post by djjazzy on 2005-05-11
I am trying to sort out problems with Evolution and Mplayer that require me to apt-get some libraries. When I try to install evolution-dev package in Synaptic (amongst others) I get a 

"could not mark all packages for installtion or upgrade"
"the following packages have unresolved depenencies"
"make sure that all required repositories are added and enabled in the preferences"

Here is my /etc/apt/sources.list

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

I'm stuck, can anyone help out here? I really am enjoying Ubuntu but need to get Evolution running right against my company's Exchange server. Thanks!

---

### Post by az on 2005-05-11
Remove the non-ubuntu repositories from your list and do an update.

From the command line, you can also do 
sudo apt-get -f install

---

### Post by linuxNewb on 2005-05-11
Try adding backports...

```


deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted


```

---

### Post by djjazzy on 2005-05-11
Thanks for the reply, I removed non-Ubuntu repositories in Synaptic then exited (no restart of Ubuntu) and tried to apt-get what I need with this result:

woodman@anubis:/etc/apt$ sudo apt-get install evolution-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  evolution-dev: Depends: libgal2.4-dev (>= 2.4.0) but it is not going to be installed
                 Depends: libgnomeui-dev (>= 2.6) but it is not going to be installed
E: Broken packages

---

### Post by az on 2005-05-11
If you want to use the ocmmand line:

sudo apt-et update
sudo apt-get -f install

---

### Post by djjazzy on 2005-05-11
Added backports, same result, I'm stuck ](*,)

---

### Post by lt_kije on 2005-05-11
[QUOTE=djjazzy]Added backports, same result, I'm stuck ](*,)[/QUOTE]
 Are you updating your apt-cache after you make changes to the repositories? I've found that Synaptic can get kind of confused sometimes -- for me, using the command line is easiest.

[code]$ sudo apt-get update; sudo apt-get upgrade
$ sudo apt-get install evolution

---

### Post by djjazzy on 2005-05-12
Tried that, still no sucess. My evolution install did work until I started playing around with it go get access to public folders on Exchange. Now I can't access the Global Address List or sucessfully send mail. I found this site which explained the authentication issues with Evolution and Exchange 03:

[https://mams.melcoe.mq.edu.au/zope/mams/pubs/Installation/evolution-exchange](https://mams.melcoe.mq.edu.au/zope/mams/pubs/Installation/evolution-exchange)

It's in trying to do the initial apt-gets that my problems occur. I'm using a m$ box still to deal with mail but am otherwise ready to pull out my hair!

---

