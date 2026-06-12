---
title: "Apt-Get Error"
date: 2005-07-18
forum: Desktop Environments
---

### Post by Geekboy on 2005-07-18
I'm getting some errors while running apt-get.  How do I fix them.  Thanks.

Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  flashplayer-mozilla libdvdcss2
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

---

### Post by Kyral on 2005-07-18
It means that something like it has to change libraries or something.

do a sudo apt-get dist-upgrade 

That will make Apt use "Smart" depend resolving, which means if the new packages need depends or it requires other packages upgrading, it will do it

---

### Post by Geekboy on 2005-07-18
Thanks for the reply.  I already tried that and no go. 

So far I tried Synaptic, Ubuntu Update Manager.

For command line Apt-get, I did an apt-get update, apt-get upgrade, apt-get dist-upgrade.  

That's about the extent that I know how to do with apt-get (still a Linux Newbie).

Here is a copy of my sources.list.  Maybe I'm missing a repository?
 ```
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

# deb http://security.ubuntu.com/ubuntu hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb ftp://ftp.nerim.net/debian-marillat/ sarge main
deb ftp://ftp.nerim.net/debian-marillat/ sid main
deb ftp://ftp.nerim.net/debian-marillat/ etch main


## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

---

### Post by mad_scientist03 on 2005-07-18
Try "sudo apt-get install  flashplayer-mozilla" and then "sudo apt-get install libdvdcss2" to see if you can get them to install manually. This has worked for me in the past. Usually the packages are held back because they have new dependencies, and apt-get does not assume that you want to install added dependencies.

---

### Post by luckyaba on 2005-07-18
Try "apt-get remove firefox" "apt-get remove mozilla-firefox" and the install "apt-get install firefox" that worked for me when i messed up firefox

---

### Post by Geekboy on 2005-07-18
I tried apt-getting the individual packages and here is what I got.

geekboy@ubuntupc:~$ sudo sudo apt-get install flashplayer-mozilla
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
  flashplayer-mozilla: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
E: Broken packages
geekboy@ubuntupc:~$ sudo apt-get install libdvdcss2
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
  libdvdcss2: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
E: Broken packages
geekboy@ubuntupc:~$

---

### Post by msh on 2005-07-19
Try

apt-get autoclean
apt-get check
apt-get update
and then 
apt-get dist-upgrade -u

---

### Post by Geekboy on 2005-07-19
Finally resolved it!  \\:D/

I took out the marillat lines out of my sources.list file.  I also remove the packages and reinstalled them.  

#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sid main
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main

---

