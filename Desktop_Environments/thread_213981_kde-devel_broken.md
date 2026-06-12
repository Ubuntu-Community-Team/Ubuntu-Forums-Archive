---
title: "kde-devel broken"
date: 2006-07-12
forum: Desktop Environments
---

### Post by 11001001 on 2006-07-12
Just when I thought my package nightmares were over...

So I'm on kde-look.org, right? I literally did a fresh install of Kubuntu (install Ubuntu server, then used apt to get kubuntu-desktop) an hour ago. I need kde-devel to build these KDE themes and install them. However, should I desire to try to use apt-get to install it, I get rewarded with this message:

```
$ sudo apt-get install kde-devel
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
  kde-devel: Depends: kdesdk but it is not going to be installed
             Depends: libartsc0-dev but it is not going to be installed
             Depends: libarts1-dev but it is not going to be installed
             Depends: kdelibs4-dev but it is not going to be installed
             Depends: kdebase-dev but it is not going to be installed
             Depends: libkonq4-dev but it is not going to be installed
E: Broken packages
```

I'm clueless.

---

### Post by croak77 on 2006-07-12
They might be updating the server. I would double check your sources.list and try again later.

---

### Post by MM23 on 2006-07-17
I have this same exact problem, and it's unimaginably frustrating. What is with the apt repositories and their dependency problems lately? My sources.list has nothing third party on it whatsoever.

---

### Post by Mithrilhall on 2006-08-03
Well...I'm a new convert from Windows and I'm having the same issue installing `kde-devel' or `kdesdk`.

Any suggestions?

:-k

---

### Post by biovore on 2006-08-03
Having simular problems here with kdesdk and kde-devel

It looks like it all stems from libqt3-mt and libqt3-mt-dev and associated packages seam to ask for conflicting versions.

3.3.6-1ubuntu3 and 3.3.6-1ubuntu6

On my one box I managed to get 3.3.6-1ubuntu6.. but when I am looking in the mirror now.. I only see 3.3.6-1ubuntu3..  Maybe a ubuntu mirror server is out of sync,..

kde-devel and kdesdk are "Virtual" packages that pull a bunch of dependencies. libqt3-mt-dev and qt3-dev-tools seem to be the problem..
that cause allot of the other packages to fail install.

](*,) 
---------------------------

Found it..   

The packages are in dapper-updates..  Add the following line to your /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main multiverse restricted universe

then sudo apt-get update
then sudo apt-get upgrade (updates a bunch of kde stuff)
then sudo apt-get install kdesdk

Worked here..  Its all about having the right repos.  =D>

---

### Post by Mithrilhall on 2006-08-03
Damn...still no go here.

Could you post your sources.list? I think I screwed mine up. :confused:

> 
eric@Innorruk:~$ sudo apt-get intall kdesdk
E: Invalid operation intall
eric@Innorruk:~$ sudo apt-get install kdesdk
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
  kdesdk: Depends: kspy (>= 4:3.5.2-0ubuntu3) but it is not going to be installed
E: Broken packages
eric@Innorruk:~$                              


---

### Post by gruffy on 2006-08-07
Hi there,

Anyone has any way around this? The adding of the US-archive into my sources.list did not make any difference at all. (I am normally on se, but I have tested a few and it is all the same.)

When I try to add libqt3-mt-dev I get this back from Synaptic:

libqt3-mt-dev:
 Depends: libxcursor-dev but it is not going to be installed
 Depends: xlibmesa-gl-dev  but it is not installable or
	libgl-dev
 Depends: libglu1-xorg-dev  but it is not installable or
 	libglu1-mesa-dev but it is not going to be installed or
	libglu-dev


And I have tried to create a new sources.list from Source-O-matic, trued update/upgrade etc. For me it seems to be some inconsistency in the package database???

Please advice...

EDIT:
I have now solved it...I as many of you out there could not resist to test compiz etc...this meant that I needed to upgrade my stuff on this as well...so I updated/upgraded with these added. In my case these:
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main

Then it replaced the "compiz-themer" to a cgwd themer and after this the libqt3-mt-dev dependencies work nice again.

Best regards
Gruffy

---

