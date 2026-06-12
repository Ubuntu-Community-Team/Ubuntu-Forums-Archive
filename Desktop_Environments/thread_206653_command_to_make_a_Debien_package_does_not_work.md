---
title: "command to make a Debien package does not work"
date: 2006-06-30
forum: Desktop Environments
---

### Post by randell6564 on 2006-06-30
Hello!

I'm trying to install a java package and the directions here: [http://www.debian-administration.org/articles/142](http://www.debian-administration.org/articles/142)  are not working.

I've tried these commands and still cant get it to work:

[B]scott@shop:~/java$ fakeroot make-jpkg jdk-1_5_0_07-linux-i586.bin
bash: fakeroot: command not found
scott@shop:~/java$ sudo make-jpkg jdk-1_5_0_07-linux-i586.bin
sudo: make-jpkg: command not found
scott@shop:~/java$ make-jpkg jdk-1_5_0_07-linux-i586.bin
bash: make-jpkg: command not found
scott@shop:~/java$ make-deb jdk-1_5_0_07-linux-i586.bin
bash: make-deb: command not found
[/B]

I know that its me!  can someone tell me just exactly what I'm suppose to enter in order to make .bin into a deb package?

Thanks!

---

### Post by bluevoodoo1 on 2006-06-30
Did you do this?

```
sudo apt-get install fakeroot java-package
```

---

### Post by randell6564 on 2006-06-30
[QUOTE=bluevoodoo1]Did you do this?

```
sudo apt-get install fakeroot java-package
```[/QUOTE]

No.  I just downloaded a .bin from sun, and followed the directions at the above sight.

Your above command is for changing .bin into deb pkg?  Thanks!

---

### Post by randell6564 on 2006-06-30
ok...

there is a jdk-1_5_0_07-linux-i586.bin in a folder named java that is in my home folder.

this is the result of sudo apt-get install fakeroot java-package:
[B]
scott@shop:~/java$ sudo apt-get install fakeroot java-package
Password:
Reading package lists... Done
Building dependency tree... Done
Package java-package is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package java-package has no installation candidate[/B]

---

### Post by az on 2006-06-30
java-package is in multiverse.  Do you have that repo enabled?

BTW sun-java5 packages are available in the multiverse repo.  You don't need to build them.

---

### Post by randell6564 on 2006-06-30
[QUOTE=azz]java-package is in multiverse.  Do you have that repo enabled?

BTW sun-java5 packages are available in the multiverse repo.  You don't need to build them.[/QUOTE]

Thats what I thought!  But I cant find it in synaptic!  And as far as multiverse being enabled, I'm quite sure that it is.

heres my sources.list:

# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
**deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse**
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
[B]deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe[/B]

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
[B]deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse[/B]

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main


Seems to all be there huh?  This is my 3rd or 4th install of ubuntu and I always had jre and jdk in synaptic before!
dont know why i cant find it.

---

### Post by az on 2006-06-30
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe main restricted multiverse

There are Dapper, Dapper-updates, Dapper-security and Dapper-backports repos.  You seem to have multiverse in the dapper-updates, backports and security, but not in dapper.

Change the above line to:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse

---

### Post by randell6564 on 2006-06-30
[QUOTE=azz]deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe main restricted multiverse

There are Dapper, Dapper-updates, Dapper-security and Dapper-backports repos.  You seem to have multiverse in the dapper-updates, backports and security, but not in dapper.

Change the above line to:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse[/QUOTE]


You're The MAN! worked like a charm!!  Wonder how that happened!

The only time that I messed with my sources.list was when I enabled everything.  And I only UN-commented where needed.

Oh well,  Thank You My friend!  Good Job!

---

