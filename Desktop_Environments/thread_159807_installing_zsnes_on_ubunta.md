---
title: "installing zsnes on ubunta"
date: 2006-04-13
forum: Desktop Environments
---

### Post by anxean on 2006-04-13
Anyone know how to get this thing to install?

---

### Post by aysiu on 2006-04-13
[QUOTE=anxean]Anyone know how to get this thing to install?[/QUOTE] Sure. [Enable extra repositories](http://www.psychocats.net/ubuntu/sources) and then ```
sudo apt-get update
sudo apt-get install zsnes
``` For more details, go here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

For the terminal, go to Applications > Accessories > Terminal

---

### Post by anxean on 2006-04-13
anxean@ubuntu:~$ sudo apt-get update
Reading package lists... Done
anxean@ubuntu:~$ sudo apt-get install zsnes
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package zsnes

i think i may be doing something wrong

---

### Post by aysiu on 2006-04-13
[QUOTE=anxean]anxean@ubuntu:~$ sudo apt-get update
Reading package lists... Done[/QUOTE] This means you have no repositories.

Take a look at this link again:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by anxean on 2006-04-13
hey very nice i got it working, but do you know how to turn on vsync?

---

### Post by aysiu on 2006-04-13
[QUOTE=anxean]hey very nice i got it working, but do you know how to turn on vsync?[/QUOTE] I don't even know what vsync is--sorry.

---

### Post by enopepsoo on 2006-04-14
you could always try snes9x

```
sudo apt-get install snes9x
```

It works quite well with roms and whatnot.

Did you try the manual for zsnes vsync info?

```
man zsnes
```
8)

---

### Post by Jason_25 on 2006-04-14
Zsnes is tremendously better for linux.  For instance, snes9x doesn't even support full screen mode.  Zsnes video options may have an option for vsync, or limiting the frame rate.

---

### Post by jon_benge on 2006-04-14
Hey this is great!

But I can't get any sound :-| 

```
MMX support found and enabled.

Sound init failed!
freq: 22050, channels: 1, samples: 256
Device 0 SAITEK P880
6 axis, 12 buttons, 0 hats, 0 balls
```

Any ideas?

---

### Post by jon_benge on 2006-04-14
Ah OK! I've found a short-term solution:

```
killall esd
```

I find that I have to enter that to get quite a few games to play with sound :???: Wolfenstein won't play with sound unless I type that.

Surely there is a more perminent way to get sounds in these games?

---

### Post by dracule on 2006-04-23
I keep trying to install zsnes but it says this
> kyle@ubuntu:~/Desktop$ sudo apt-get install zsnes
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libstdc++6: Depends: gcc-4.1-base (= 4.1.0-1+b1) but it is not installable
              Depends: libc6 (>= 2.3.6-6) but 2.3.5-1ubuntu12.5.10.1 is to be installed
              Depends: libgcc1 (>= 1:4.1.0) but 1:4.0.1-4ubuntu9 is to be installed
W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
when i try to upgrade them the say i need more dependancies and when i try to upgrade those the say i need the depedancy that i just tried to upgrade but couldnt becuase i needed the other one.

---

### Post by itazuki on 2006-05-03
[QUOTE=aysiu]Sure. [Enable extra repositories](http://www.psychocats.net/ubuntu/sources) and then ```
sudo apt-get update
sudo apt-get install zsnes
``` For more details, go here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

For the terminal, go to Applications > Accessories > Terminal[/QUOTE]

i think i have the extra repositories added but i still don't have zsnes in synaptic. Here's my sources.list


deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse 
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse  

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse 
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse  

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse  

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse 
# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse  

# deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main 

# deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

any ideas on what's wrong?

---

