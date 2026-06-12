---
title: "Using CD-ROM as source for applications (I'm new to Ubuntu)"
date: 2005-10-21
forum: Desktop Environments
---

### Post by sammyh00 on 2005-10-21
How do you load additional programs/software from cd-rom with this OS?

---

### Post by DJ_Max on 2005-10-21
By default your only source is your CDROM. Install software via Synaptic.

---

### Post by fimbulvetr on 2005-10-21
I think, perhaps, the person is a bit newer than that.

sammyh00, assuming you're using ubuntu (not kubuntu), there's a number of icons on your top bar to the left. Hold your mouse over these to see a description. Find the one call synaptic package manager. This is what you want. Bring it up, browse, search and have fun.

After your package of choice is done installing, check your menu bar (Applications to see if it showed up.). If you didn't, let us know on the forums and we can probably help you. If you know what you want, but can't find it, let us know on the forums.

---

### Post by sammyh00 on 2005-10-21
I'm missing something guys.I'm trying to load programs that didn't come with Ubuntu. I had already found the program that you mentioned but can not figure how to load from there.Like I said I am completely new to Ubuntu.
Thanks

---

### Post by heart_reaver on 2005-10-21
Open Synaptics,

1) Look for menu called repositories
2)Click to it.
3)There will an option **ADD**
4)Check this out to add CD's as sources


>>> I am writting this reply working over gentoo so bare with me if i am bit or byte wrong. I will update as soon i log on to ubuntu if its required.;)

---

### Post by nolan43 on 2005-10-26
Hi, I'm new to Linux and Ubuntu; and I rerased WinXp :rolleyes: . My problem is I followed the direction to add a new repository, and now my Add Applications is BLANK. I've tried to find how to reload it for the last couple of days:( :mad: with no success. I need HELP all this is new to me:confused:

---

### Post by Casey on 2005-10-26
[QUOTE=nolan43]Hi, I'm new to Linux and Ubuntu; and I rerased WinXp :rolleyes: . My problem is I followed the direction to add a new repository, and now my Add Applications is BLANK. I've tried to find how to reload it for the last couple of days:( :mad: with no success. I need HELP all this is new to me:confused:[/QUOTE]

The first thing to check and easiest thing to fix, would be if you simply needed to reload the list.  To do this go to System->Administration->Update Manager and click reload.  Does that give any errors? If so -- post them.  Also does that now allow you to add applications?

If not... read on:
It is my best guess that you have accidentily altered your list of sources by editing the repositories by hand.  I can give you a list of instructions that will get them back for you, but I do not have a default list of sources.  Therefore I would be giving you my sources.list (which contains every available official ubuntu source).  If someone can post a default sources.list file here, I can give you a list of instructions to get things back to how they were when you started.  If they don't by the time you try the first fix and the first fix fails, I will post the instructions + my sources.list.

A call out to all people reading this message: If you have a default copy of the sources, please open a terminal and type this: 
```
cat /etc/apt/sources.list
```
and post the output here.

Thanks!

---

### Post by Beggar on 2005-10-26
Im almost positive this is the default source list :

[i]deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

#nope not default, my bad ;)
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

[/i]

---

### Post by psychicdragon on 2005-10-26
The default sources.list looks something like this:
```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted  

deb http://us.archive.ubuntu.com/ubuntu/ breezy main restricted   
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy main restricted   

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted   
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted    

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ breezy universe      
# deb-src http://us.archive.ubuntu.com/ubuntu/ breezy universe      

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse      
# deb-src http://us.archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted     
deb-src http://security.ubuntu.com/ubuntu/ breezy-security main restricted 


```

Run ```
sudo gedit /etc/apt/sources.list
``` and paste those sources over the ones that were in there.

Then run ```
sudo apt-get update
``` to update apt's package list.

Now you should be able to install software again.

---

