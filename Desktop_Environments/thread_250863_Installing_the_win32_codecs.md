---
title: "Installing the win32 codecs"
date: 2006-09-04
forum: Desktop Environments
---

### Post by Sir_Sid on 2006-09-04
Im having some trouble installing the win 32 codecs. Im using the command I found in the documentation at help.ubuntu.com but all i get is a buncha erorrs and then a buch of giberish which isnt even in englishs. Its like a buch of symbols. Any Ideas?

---

### Post by taurus on 2006-09-04
I believe you need to enable both universe & multiverse by removing the # sign in /etc/apt/sources.list to get the codecs.  So, open a terminal, Applications -> Accessories -> Terminal, and edit it with

```
gksudo gedit /etc/apt/sources.list
```
Then, try to update it and install your codecs again...

---

### Post by patagonik on 2006-09-04
Try with thisone... [http://ubuntuguide.org/wiki/Dapper#How_to_use_Easy_Ubuntu](http://ubuntuguide.org/wiki/Dapper#How_to_use_Easy_Ubuntu) 
It allows you to install the codecs easyly! It also tells you how to add new repositories so you can download those codecs.

---

### Post by Sir_Sid on 2006-09-04
> **taurus said:**
> I believe you need to enable both universe & multiverse by removing the # sign in /etc/apt/sources.list to get the codecs.  So, open a terminal, Applications -> Accessories -> Terminal, and edit it with

```
gksudo gedit /etc/apt/sources.list
```
Then, try to update it and install your codecs again...

By multiverse do you mean backports?

---

### Post by Ultra-Loser on 2006-09-04
Once you open the sources.list, there will be something that says "uncomment the following two lines to add software from the 'universe' repository..."  That means you just remove the # signs in front of the lines below it that look somewhat like this:

```
# deb http://tw.archive.ubuntu.com/ubuntu dapper universe multiverse
# deb-src http://tw.archive.ubuntu.com/ubuntu dapper universe multiverse
```

That will enable both the universe and multiverse repositories. 

Alternatively, if you want to do it the non-text-editing way, you could go into synaptic, then hit settings > repositories and tick the "Ubuntu 6.06 LTS" boxes that say "community maintained (universe)" and "Non-free (miltiverse)" under them. 

Hope that's clear.

---

### Post by Sir_Sid on 2006-09-05
I dont think I see what you  are talking about. Here I will just post what is in my list.


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


The only one with multiverse is backports

---

### Post by Sir_Sid on 2006-09-06
Bump!

---

### Post by Sir_Sid on 2006-09-10
Please anybody which item should I uncomment. I do not see the one he wants

---

### Post by astoltz on 2006-09-10
The w32codecs package is not in any of the repositories.  You need to download and install it manually.  See the [wiki page]("https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5") for a good explaination

---

### Post by Sir_Sid on 2006-09-10
Well it wants some unofficial repositories. Which repositories are those?

---

### Post by astoltz on 2006-09-11
You just have to manually download the package - no need to add any un-offical repositories to your sources.lst.   Open a terminal and paste the following command: ```
wget -c http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb
```
That will download the file w32codecs_20060611-1plf1_i386.deb to your home directory.  After the wget command finishes, the next line will install it for you: ```
sudo dpkg -i w32codecs_20060611-1plf1_i386.deb
```
sudo will ask you for your password.  After that one is done, you should be all set.  You can delete the deb file if you want to - it's just taking up space now.

---

