---
title: "&quot;apt-get upgrade&quot; problem again"
date: 2005-09-11
forum: Desktop Environments
---

### Post by acim on 2005-09-11
Hello,
I am using Kubuntu.

I've asked a special question, but I think I had a lack of explaining. 
I want to tell you that what is happening when I want to make "apt-get" and "apt-get upgrade".
1) I am writing down "apt-get update" in the terminal panel.
OK. No problem.

2) Then I am writing "apt-get upgrade"
Now. Please take care!
What do I see when I write down "apt-get upgrade"? Here it is:

[B]root@AcimKubuntuLinux:/home/sacim # apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  acroread acroread-plugins amarok amarok-arts firefox foomatic-db-hpijs
  foomatic-filters-ppds gimp gimp-data gimp-svg gtk2-engines-clearlooks hpijs
  k3b k3blibs konversation libgcc1 libgimp2.0 libsmbclient mozilla-acroread
  mozilla-firefox powernowd python-xdg python2.4-samba samba-common smbclient
  w32codecs
26 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/104MB of archives.
After unpacking 262MB disk space will be freed.
Do you want to continue [Y/n]?[/B]        

I press enter key. Then I see this:

[B]Do you want to continue [Y/n]?
WARNING: The following packages cannot be authenticated!
  libgcc1 acroread acroread-plugins amarok-arts amarok mozilla-firefox firefox
  hpijs foomatic-db-hpijs gimp-data libgimp2.0 gimp gimp-svg
  gtk2-engines-clearlooks k3blibs k3b konversation mozilla-acroread powernowd
  python-xdg python2.4-samba samba-common smbclient w32codecs
  foomatic-filters-ppds libsmbclient
Install these packages without verification [y/N]?[/B]    

When I press "y" key, it comes:

[B]Install these packages without verification [y/N]? y
E: Some packages could not be authenticated
root@AcimKubuntuLinux:/home/sacim #[/B]          

"Some packages could not be authenticated". 

My question is:

What should I do to authenticate the packages? Or what are the ways of authentication for these packages?

Because, I can't upgrade the relevant packages, so my siystem turns to an old system.

I think, this time &#305; accomplished to explain my problem.

I am adding my "sources.list" below for giving an idea to find a solution.

_This is my sources.list:_

[B]# deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

#### backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted 

##Kubuntu
deb [http://kubuntu.org/hoary-kde342/](http://kubuntu.org/hoary-kde342/) hoary-updates main 
deb-src [http://kubuntu.org/hoary-kde342/](http://kubuntu.org/hoary-kde342/) hoary-updates main[/B]

---

### Post by f1dave on 2005-09-11
Well, the first thing i notice is that you are root.

This shouldn't really be done under ubuntu afaik. Although I do not know if this is related to your problem. The 'authenticated' refers to the fact that the packages are not part of the original ubuntu release, they are 3rd party ones or backports, etc. This doesn't really mean that they will not function of course.

---

