---
title: "Update Vis Synaptic Not Wotking"
date: 2006-08-11
forum: Desktop Environments
---

### Post by WorkingOnGoingLinux on 2006-08-11
I tried adding a location for systemimage now I get this eror message whenI try to upgrade.
HOW DO I FIX IT ??

THANKS

E: Type 'http://download.systemimager.org/debian' is not known on line 29 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.

---

### Post by ciscosurfer on 2006-08-11
Exactly what are you trying to do? :D

---

### Post by WorkingOnGoingLinux on 2006-08-11
I got a notification that an upgrade is available but when I click the little orange icon I can't upgrade I get this error message posted above. I need to go back and remove the reference to sysetemimage. I was trying to downlaod that program this morning. Obviously the link must be bad.
How do I get this area? "Go to the repository dialogue to correct the problem

---

### Post by ciscosurfer on 2006-08-11
You need your universe repo enabled to grab from Ubuntu Dapper repos.

That link is not bad, I just checked it (but it's in the debian archive, and while Ubuntu is a debian sysytem, you should always try to use the packages relating to your specific sytem and version, i.e, ubuntu dapper).  

But the package 'systemimager' is in the dapper universe repos as well.  Why not try updating that way?  Just enable your universe repo and then do```
sudo aptitude update && sudo aptitude upgrade
``` 

If I'm misunderstanding you, please explain again :grin:

Also, please post your sources.list```
cat /etc/apt/sources.list
```

---

### Post by WorkingOnGoingLinux on 2006-08-11
RESULTS FROM ENTERING >>sudo aptitude update && sudo aptitude upgrade

: Type 'http://download.systemimager.org/debian' is not known on line 27 in source list /etc/apt/sources.list
E: Type 'http://download.systemimager.org/debian' is not known on line 27 in source list /etc/apt/sources.list
E: The list of sources could not be read.
skip@emptybox:~$




RESULTS FROM>>cat /etc/apt/sources.list

kip@emptybox:~$ cat /etc/apt/sources.list

# Line commented out by installer because it failed to verify:
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
[http://download.systemimager.org/debian](http://download.systemimager.org/debian) stable main
/etc/apt/sources.list

skip@emptybox:~$ 

thanks for your help here

---

### Post by ciscosurfer on 2006-08-11
Change the last line in your souces.list file from```
[http://download.systemimager.org/debian](http://download.systemimager.org/debian) stable main
```to```
deb [http://download.systemimager.org/debian](http://download.systemimager.org/debian) stable main
deb-src [http://download.systemimager.org/debian](http://download.systemimager.org/debian) stable main
```The second line is for sources if you want to compile it...otherwise, the first line is where it'll grab the program.  So change the last line to what I have above and then do again[sudo aptitude update && sudo aptitude upgrade[/code]

---

### Post by WorkingOnGoingLinux on 2006-08-11
Ok thanks
But how do I make the changes ?
I don't know how to edit it.

---

### Post by eXcentra on 2006-08-11
> **WorkingOnGoingLinux said:**
> Ok thanks
But how do I make the changes ?
I don't know how to edit it.
```
sudo gedit /etc/apt/sources.list
```

---

### Post by WorkingOnGoingLinux on 2006-08-12
Problem Fixed.

Many thanks to ciscosurfer & eXcentra.
This is what I love about using linux especially
Ubuntu. Perfect strangers helping each other.

Too bad the world didn't work this way. Sure would
be a lot less anger and loss of life in the world.  

I will be changing my name soon to I'm on Linux full time.

---

### Post by ciscosurfer on 2006-08-12
I'm glad you got it all straightened out.  Let us know if we can be of any further assistance! 
:D

---

