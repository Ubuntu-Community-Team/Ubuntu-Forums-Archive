---
title: "Dependency Hell"
date: 2006-07-09
forum: Desktop Environments
---

### Post by 11001001 on 2006-07-09
Alright, I've royally screwed something up. I'm using Kubuntu 6.06 and while I tried to get dvd::rip working, I attempted to install some packages that it said it was missing, like libc6. Now, if I need to build something, like GTK# , when I run ./configure, it tells me "C compiler cannot create executables". So I looked on other forums and tried to (re)install gcc and glib and libc, and this is what Konsol will produce:

```

frank@ChuckNorris:~$ sudo apt-get install build-essential
Password:
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
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages
frank@ChuckNorris:~$ sudo apt-get install libc6-dev
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
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6-15 is to be installed
E: Broken packages
frank@ChuckNorris:~$ sudo apt-get install libc-dev
Reading package lists... Done
Building dependency tree... Done
Note, selecting libc6-dev instead of libc-dev
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6-15 is to be installed
E: Broken packages

```

As a Linux newbie in general, I just fouled up things in general. I desperately need any and all advice.

---

### Post by taurus on 2006-07-09
Try
```

sudo apt-get update
sudo apt-get install build-essential

```

---

### Post by 11001001 on 2006-07-09
That takes me into another loop of broken dependencies:

```
frank@ChuckNorris:~$ sudo apt-get install build-essential
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
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages
frank@ChuckNorris:~$ sudo apt-get install g++
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
  g++: Depends: g++-4.0 (>= 4.0.3) but it is not going to be installed
E: Broken packages
frank@ChuckNorris:~$ sudo apt-get install g++-4.0
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
  g++-4.0: Depends: libstdc++6-4.0-dev (= 4.0.3-1ubuntu5) but it is not going to be installed
E: Broken packages
frank@ChuckNorris:~$ sudo apt-get install libstdc++6-4.0-dev
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
  libstdc++6-4.0-dev: Depends: libc6-dev (>= 2.3.5-1ubuntu5) but it is not going to be installed
E: Broken packages
frank@ChuckNorris:~$ sudo apt-get install libc6-dev
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
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6-15 is to be installed
E: Broken packages

```

---

### Post by DJ Scribblinni on 2006-07-09
Nice computer name...:| 
Just out of curiosity what happens when you do a ```
sudo apt-get install build-essential
```

EDIT: Two people did something by the time it took me to post this....


How about ```
sudo apt-get -f install
```

---

### Post by 11001001 on 2006-07-09
```
frank@ChuckNorris:~$ sudo apt-get install build-essential
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
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages
frank@ChuckNorris:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
frank@ChuckNorris:~$
                                                     
```

---

### Post by taurus on 2006-07-09
What does your /etc/apt/sources.list look like anyway?

```

more /etc/apt/sources.list

```

Is this a fresh install or an upgrade?

---

### Post by 11001001 on 2006-07-09
```

# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://www.beerorkid.com/automatix/apt dapper main
deb http://archive.canonical.com/ubuntu dapper-commercial main

```

This is a fresh install from Ubuntu, with the kubuntu-desktop package added.

---

### Post by taurus on 2006-07-09
I would comment out the two lines for "dapper-backports" by placing a # in front of them and the last two lines in your /etc/apt/sources.list as well...  Then

```

sudo apt-get update
sudo apt-get install build-essential

```

---

### Post by 11001001 on 2006-07-09
Nope, still nothing. I get the same error from apt-get as I did before I commented out the backports. Well, this is what I get for messing around with stuff I don't understand.

---

### Post by taurus on 2006-07-09
Just so you know, build-essential is on the CD so you can tell synaptic to look for it on your CD or add CD to your repos...

---

### Post by 11001001 on 2006-07-09
My only problem is that Ubuntu says that I can't install any of the dependencies that build-essential needs. It keeps telling me that I have an "impossible request" or something along those lines. If I try to do an apt-get uninstall glibc, it tells me that pretty much every package on my system is dependent on it. I think I have a non-Ubuntu version on my system, and it won't let me roll it back. I think I saw something in Synaptic a while back about marking something for reinstallation, so I'll probably try that.

---

### Post by Xiata on 2006-07-09
Periodically I've noticed the us.archive servers are retarded. Try changing all the us.archive.ubuntu.com to archive.ubuntu.com in your /etc/apt/sources.list.

---

### Post by aysiu on 2006-07-09
I would do this:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

That'll get you a fresh sources.list *and* back up your old one.

Then do ```
sudo aptitude update
sudo aptitude install build-essential
```

If you want your old sources.list back afterwards, you can always do this: ```
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list
```

---

### Post by koshari on 2006-07-09
is there any reason why you cant use synaptic to repair any broken packages, install the package you want and meet all you dependencies?

---

### Post by 11001001 on 2006-07-09
I think I figured out my problem. 

I originally couldn't find "glibc6" through Apt, so I ended up doing a Google search for it and downloading the version off of the Debian public package server. That didn't jibe with the rest of the development packages, so after much futzing around, I found glibc6 on Ubuntu's servers and used Kpackage to force the package to downgrade to Ubuntu's official package. After that, build-essential installed without a hitch. Thanks for all your suggestions!

---

### Post by trevdiggy on 2006-07-13
> **aysiu said:**
> I would do this:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

That'll get you a fresh sources.list *and* back up your old one.

Then do ```
sudo aptitude update
sudo aptitude install build-essential
```

If you want your old sources.list back afterwards, you can always do this: ```
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list
```


aysiu, thanks for some excellent advice.  I had a broken libc6 package problem that caused Synaptic to think a whole bunch of packages depended on libc6.  It was a real pain.  I found your suggestions here and tried them.  Problem solved.

---

### Post by amerikkanu on 2007-01-15
> **11001001 said:**
> I think I figured out my problem. 

I originally couldn't find "glibc6" through Apt, so I ended up doing a Google search for it and downloading the version off of the Debian public package server. That didn't jibe with the rest of the development packages, so after much futzing around, I found glibc6 on Ubuntu's servers and used Kpackage to force the package to downgrade to Ubuntu's official package. After that, build-essential installed without a hitch. Thanks for all your suggestions!

I have almost exactly the same problem and am wondering how to get Kpackage or Synaptic to downgrade to an older version of a package on the repositories (all I can see now is the newer installed one)?

In my case, I wanted to install audacious, but in putting on one of its dependencies, a newer version of fontconfig-config, i broke libfontconfig1.  here's the error when i try to fix the latter:

$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libfontconfig1: Depends: fontconfig-config (= 2.3.2-7ubuntu2) but 2.4.2-1 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

and to remove fontconfig-config requires over 500 packages also to be removed.  ](*,)

---

