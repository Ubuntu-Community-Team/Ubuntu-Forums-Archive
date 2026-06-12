---
title: "synaptic is brain dead"
date: 2007-05-12
forum: Desktop Environments
---

### Post by dawhistler on 2007-05-12
My synaptic has gone south...the screen comes up, asks for my password then fades away...
I tried Add/Remove program from under Applications but it followed synaptic and does not work either.  Is there a process by which I can repair both of these apps?
I am running Fiesty

mas

---

### Post by earobinson on 2007-05-12
```
sudo apt-get update
sudo apt-get upgrade
```

let us know how it goes

---

### Post by dawhistler on 2007-05-12
I tried apt-get update and it froze at 59%

I waited a bit and tried it again only this time it replied. ...resources temporarily unavailable

---

### Post by taurus on 2007-05-12
You should post the command and the whole message after you run that command.  It makes it much easier to diagnose the problem.

---

### Post by dawhistler on 2007-05-12
In terminal I entered
sudo apt-get update



I received this message...
Fetched 196B in 2s (92B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... 59% 

The terminal freezes at this point.


If I shut down the terminal and try again I get this message...
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
mas@mas-desktop:~$

After rebooting the machine I tried once again to enter the commands in terminal and got the same results


mas

---

### Post by taurus on 2007-05-12
Are you running Feisty or Dapper?  Can you post your /etc/apt/sources.list here?

```
cat /etc/apt/sources.list
```

---

### Post by dawhistler on 2007-05-12
I am running Feisty...

here is the response 


## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review


## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

 ## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
mas@mas-desktop:~$

---

### Post by taurus on 2007-05-12
Then how come you have all those edgy/dapper repos in your /etc/apt/sources.list?

Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove everything in in.  Then, add these lines in for your new repos.

```

deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

deb http://archive.ubuntu.com/ubuntu feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

```
Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by dawhistler on 2007-05-12
Taurus...
earobinson...

Thanks...

The community support found here at Ubuntu Forums has been superb and professional...you guys rock!
I can only hope to help out myself sometime.  
I am trying to learn as much as possible about the Linux os and have found that I learn best by diving in...I am now aware of upgrade links and such and that they should be matching your os version...
My only other issues have to do with printing.  I will scour the forums and if I can not find a resolution...I will give a yell.


Thanks once again.



mas

---

### Post by earobinson on 2007-05-15
np

---

