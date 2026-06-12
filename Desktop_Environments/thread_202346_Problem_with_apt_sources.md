---
title: "Problem with apt sources?"
date: 2006-06-23
forum: Desktop Environments
---

### Post by al_mckin on 2006-06-23
Hi everyone,

I think I have a problem with my apt-get sources.list.  

I previosly installed gcc-3.4 on breezy (by downloading it from packages.ubuntu.com) and then I upgraded to dapper.  Now I need to install gcc-4.0, gfortran and g77.

Now to the problem, when I run "apt-get install g77" I get this message:

Reading package lists... Done
Building dependency tree... Done
Package g77 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package g77 has no installation candidate

I was going to go and download the packages by hand, but this problem is annoying me!  Any suggestions? I posted my sources.list at the bottom of this mail.

Best regards,

Alastair


# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ dapper main restricted



## Uncomment the following two lines to fetch updated software from the network

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse


deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


deb [http://www.paul.sladen.org/debian](http://www.paul.sladen.org/debian) all skype
deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/

---

### Post by jimbob on 2006-06-23
Try running  #apt-get build-dep g77 and see if it can resolve the dependencies.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by al_mckin on 2006-06-23
> **jimbob]Try running  #apt-get build-dep g77 and see if it can resolve the dependencies.
&#65279 said:**
> [SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]


Thanks for the idea jimbob, still get this error.  For some reason it seems that apt-get doesnt know about the gcc packages I want, thats why I thought it might have been a problem with the sources.list


alastair@colenso:~$ sudo apt-get build-dep g77
Password:
Reading package lists... Done
Building dependency tree... Done
E: Build-Depends dependency for g77 cannot be satisfied because the package m4 cannot be found


Alastair

---

### Post by Jucato on 2006-06-23
the problem probably isn't with apt, but with the package that you are using.
g77 is a metapackage that is supposed to install the default GNU Fortran 77 compiler ([http://packages.ubuntu.com/dapper/devel/g77)](http://packages.ubuntu.com/dapper/devel/g77)), which is g77-3.4

How about trying sudo apt-get install g77-3.4?

---

### Post by al_mckin on 2006-06-23
[QUOTE=Fenyx]the problem probably isn't with apt, but with the package that you are using.
g77 is a metapackage that is supposed to install the default GNU Fortran 77 compiler ([http://packages.ubuntu.com/dapper/devel/g77)](http://packages.ubuntu.com/dapper/devel/g77)), which is g77-3.4

How about trying sudo apt-get install g77-3.4?[/QUOTE]

Thanks fenyx,

Unfortunately I still get this:

alastair@colenso:~$ sudo apt-get install g77-3.4
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package g77-3.4


Alastair

---

### Post by Jucato on 2006-06-23
Ok, I think there really might be a slight problem in your sources.list after all. Sorry if I overlooked it.

Near the end of your sources.list you have this:
> 
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse


which is basically a duplicate of somethings you already have. Delete those two lines, then add the word multiverse to these two lines that you already have:

> 
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper universe


run sudo apt-get update, then try again. 

Hope it works.

---

### Post by al_mckin on 2006-06-23
[QUOTE=Fenyx]Ok, I think there really might be a slight problem in your sources.list after all. Sorry if I overlooked it.

Near the end of your sources.list you have this:


which is basically a duplicate of somethings you already have. Delete those two lines, then add the word multiverse to these two lines that you already have:



run sudo apt-get update, then try again. 

Hope it works.[/QUOTE]


Hi Fenyx, 

Thanks again, tried that and ended up with the same error:


alastair@colenso:~$ sudo apt-get update
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://www.paul.sladen.org](http://www.paul.sladen.org) all Release.gpg
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Ign [http://www.paul.sladen.org](http://www.paul.sladen.org) all Release
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Ign [http://www.paul.sladen.org](http://www.paul.sladen.org) all/skype Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources
Hit [http://www.paul.sladen.org](http://www.paul.sladen.org) all/skype Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/multiverse Sources
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Fetched 568B in 13s (42B/s)
Reading package lists... Done
alastair@colenso:~$ sudo apt-get install g77-3.4
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package g77-3.4
alastair@colenso:~$

What repository are the devel packages supposed to be contained in?

Alastair

---

### Post by Jucato on 2006-06-23
Hmm... this is also confusing me. I don't know what else to say...
g77-3.4 is supposed to be in dapper main. Have you tried using Synaptic and looking for it there?

You could try going to [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) through your web browser and manually check if the g77 packages are there.

EDIT: I just checked your server's repositories. the g77 packages are there: [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/)

Maybe you could try g77 again instead of g77-3.4? But one thing that strikes me as unusual is that you're getting some GPG errors on the regular repositories

---

### Post by ifokkema on 2006-06-23
What happens when you run:
```
apt-cache showpkg g77
```
or
```
apt-cache policy g77
```

Can you find the package when searching for it:
```
apt-cache search g77
```

---

### Post by al_mckin on 2006-06-24
[QUOTE=ifokkema]What happens when you run:
```
apt-cache showpkg g77
```
or
```
apt-cache policy g77
```

Can you find the package when searching for it:
```
apt-cache search g77
```[/QUOTE]


Hi ifokkema,

Heres what happens after I did what you said.


alastair@colenso:~$ sudo apt-cache showpkg g77
Package: g77
Versions:

Reverse Depends:
  scilab,g77
  pgplot5,g77
Dependencies:
Provides:
Reverse Provides:


alastair@colenso:~$ sudo apt-cache policy g77
g77:
  Installed: (none)
  Candidate: (none)
  Version table:
alastair@colenso:~$ sudo apt-cache search g77
alastair@colenso:~$

If I do a search for g77 in Synaptic, nothing shows up.  

If I search for fortran, I get gdb, libgtksourceview-common and pgplot5, so some of the devlopement packages are showing up.



Anyone any ideas?  

Alastair

---

### Post by ifokkema on 2006-06-24
[QUOTE=al_mckin]Anyone any ideas?  

Alastair[/QUOTE]
I think I have your problem fixed now!!!

I installed your sources list on my PC. And guess what... errors while retreiving the packages list of 'main'.... where g77 resides in. I don't know why the errors are not on your screen, but I got it fixed by using different mirrors. **The server in your sources.list is currently not working correctly.**

Fix:
```
sudo gedit /etc/apt/sources.list
```
go to Search -> Replace and replace all instances of 'gb.archive' to 'uk.archive'.
Save your file, and close gedit.
```
sudo apt-get update
sudo apt-get install g77
```

Done... :)

---

### Post by al_mckin on 2006-06-24
[QUOTE=ifokkema]I think I have your problem fixed now!!!

I installed your sources list on my PC. And guess what... errors while retreiving the packages list of 'main'.... where g77 resides in. I don't know why the errors are not on your screen, but I got it fixed by using different mirrors. **The server in your sources.list is currently not working correctly.**

Fix:
```
sudo gedit /etc/apt/sources.list
```
go to Search -> Replace and replace all instances of 'gb.archive' to 'uk.archive'.
Save your file, and close gedit.
```
sudo apt-get update
sudo apt-get install g77
```

Done... :)[/QUOTE]


Ifokkema, you legend, thanks for all your help it worked perfectly!

A strange problem indeed, thanks again!

---

