---
title: "apt-get install gcc problem!!!"
date: 2005-10-14
forum: Desktop Environments
---

### Post by webhead on 2005-10-14
Hey all,

I need gcc to install some items, however when I run ```
sudo apt-get install gcc
``` I get a dependency error.  I read someplace else that using ```
sudo apt-get install build-essential
``` would get it, and resolve dependencies too.

However, I've tried the above, and I get an error, shown below.  Have I done something wrong?

```

sudo apt-get install build-essential
Password:***************
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
                   Depends: gcc (>= 4:4.0) but it is not going to be installed
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages
```

Any ideas?

Dan

---

### Post by Dr. Nick on 2005-10-14
have you ran apt-get update? If you try to install libc6-dev by itself what dependency is missing then ? Ive had this happen wth other packages and just had to try to track down which dependency was messing it up, is this a fresh install or have you had it awhile, alot of times this is caused by incorrect repository settings or mixing alot of different versions of packages


EDIT
Your not alone look here for further discussion, it may help some, I havent had to instal this in breezy since I had it already and it just updated
[http://ubuntuforums.org/showthread.php?t=75596](http://ubuntuforums.org/showthread.php?t=75596)

---

### Post by webhead on 2005-10-14
I have run ```
apt-get update
``` and get similar errors, see below.  This is a farley fresh install (two days ago).  Is this due to the heavey load on the servers maybe?```
sudo apt-get update
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release
Get:1 http://archive.ubuntu.com hoary Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release
Ign http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
Hit http://archive.ubuntu.com hoary Release
Ign http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Err http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
  404 Not Found
Hit http://archive.ubuntu.com hoary/multiverse Packages
Err http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
  404 Not Found
Hit http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Hit http://archive.ubuntu.com hoary/multiverse Sources
Get:2 http://security.ubuntu.com hoary-security Release.gpg [189B]
Get:3 http://security.ubuntu.com hoary-security Release [16.9kB]
Get:4 http://us.archive.ubuntu.com hoary Release.gpg [189B]
Get:5 http://us.archive.ubuntu.com hoary-updates Release.gpg [189B]
Hit http://us.archive.ubuntu.com hoary Release
Hit http://us.archive.ubuntu.com hoary-updates Release
Ign http://us.archive.ubuntu.com hoary-updates Release
Hit http://us.archive.ubuntu.com hoary/main Packages
Hit http://us.archive.ubuntu.com hoary/restricted Packages
Hit http://us.archive.ubuntu.com hoary/main Sources
Hit http://us.archive.ubuntu.com hoary/restricted Sources
Hit http://us.archive.ubuntu.com hoary/universe Packages
Hit http://us.archive.ubuntu.com hoary/universe Sources
Hit http://us.archive.ubuntu.com hoary-updates/main Packages
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages
Hit http://us.archive.ubuntu.com hoary-updates/main Sources
Hit http://us.archive.ubuntu.com hoary-updates/restricted Sources
Hit http://security.ubuntu.com hoary-security/main Packages
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://security.ubuntu.com hoary-security/universe Sources
Fetched 17.2kB in 4s (3513B/s)
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main /binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/univ erse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/mult iverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/rest ricted/binary-i386/Packages.gz  404 Not Found
Reading package lists... Done
W: GPG error: http://us.archive.ubuntu.com hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signin g Key <ftpmaster@ubuntu.com>
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary -backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dist s_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory )
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary -backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_ dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or d irectory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary -backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary -backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used  instead.
```
Also, here's my /etc/apt/sources.list```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted

deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```
Thanks in advance,

Dan

---

### Post by Dr. Nick on 2005-10-14
Oh your using Hoary sources from the internet and a breezy source from cd. Thats the problem I bet. Change hoary to breezy in the sources.list and re run "update" I would comment out the backport lines too


Here is my breezy source list without the cd since I updated online
```
deb http://us.archive.ubuntu.com/ubuntu/ breezy main restricted multiverse universe   
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy main restricted   multiverse universe   

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted multiverse universe   
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted  multiverse universe   

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ breezy universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy universe 

deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted multiverse universe  
deb-src http://security.ubuntu.com/ubuntu/ breezy-security main restricted   multiverse universe   

deb http://security.ubuntu.com/ubuntu/ breezy-security universe 
deb-src http://security.ubuntu.com/ubuntu/ breezy-security universe 
```

---

### Post by webhead on 2005-10-14
[QUOTE=Dr. Nick]Oh your using Hoary sources from the internet and a breezy source from cd. Thats the problem I bet. Change hoary to breezy in the sources.list and re run "update" I would comment out the backport lines too[/QUOTE]

Oh crap, I didn't even notice!

Is it as simple as changing the word "hoary" to "breezy" or more to it?

Dan

---

### Post by Dr. Nick on 2005-10-14
thats it, hoary to breezy than sudo apt-get update to get the new list and then try again. Its a version conflict by installing older version while newer ones are their already

---

### Post by webhead on 2005-10-14
[QUOTE=Dr. Nick]thats it, hoary to breezy than sudo apt-get update to get the new list and then try again. Its a version conflict by installing older version while newer ones are their already[/QUOTE]

Cool.......well that was sure a NOOB mistake there!

gcc is on there, and I can now scan again!  :D  

Dan

---

