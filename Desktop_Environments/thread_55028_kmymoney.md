---
title: "kmymoney"
date: 2005-08-07
forum: Desktop Environments
---

### Post by dr1445 on 2005-08-07
greetings forum
i did an apt-get for synaptic, as knaptic lacks a search function. i would like to install kmymoney but the search comes up empty and apt-get can not find. i did find a source for kmymoney kubuntu deb. is there a way to upgrade the repositories, other distro's list stable,unstable,testing. if not, a how to download kmymoney deb and install, or a way to point apt-get to the download site.
regards
dave

---

### Post by coolclassic on 2005-08-07
You will need the universe repositiesL

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary universe 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 


You wiil find kmymoney in >utillities (universe)

---

### Post by Worzel on 2005-08-07
Or you can download the latest version from sourceforge -

[http://prdownloads.sourceforge.net/kmymoney2/](http://prdownloads.sourceforge.net/kmymoney2/)
kmymoney2-0.7.5-1.kubuntu5.04.i386.deb?download

Note!! the above should be all one line!! Install with dpkg.

I think Kubuntu is still at version 0.6.4. The newer Kmymoney is a great improvement.
JIm

---

### Post by dr1445 on 2005-08-07
ok, i did the universe thing and got v 6.4. i downloaded v 7.5 to the desk top, how do i use dpkg to install. when i tried v 7.5 in mepis there were some dependency problems with two files, but mepis is 3.3.
regards
dave

---

### Post by Worzel on 2005-08-08
dpkg -i <progname> and have a look at the man page and perhaps here -
[http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html)

I'm actually using 0.7.4 which installed with no problems.
Jim

---

### Post by Bob D. on 2005-08-10
[QUOTE=dr1445]ok, i did the universe thing and got v 6.4. i downloaded v 7.5 to the desk top, how do i use dpkg to install. when i tried v 7.5 in mepis there were some dependency problems with two files, but mepis is 3.3.
regards
dave[/QUOTE]
Dave,

I built that Kubuntu KMyMoney deb you got from their website using CheckInstall. I'm pretty sure it's only going to install to Kubuntu. You also may need to have KDE updated to 3.4.2 as that is the version I'm running and built the package under. I've reinstalled this 0.7.5 deb several times on my system and it work every time.

As Worzel says, to install just navigate (in a console) to the directory where you have the deb. Then a 'dpkg -i kmymoney2-0.7.5-1.kubuntu5.04.i386.deb' will install for you.

Bob

---

