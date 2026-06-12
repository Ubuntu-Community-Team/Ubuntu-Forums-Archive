---
title: "No new updates?"
date: 2006-09-02
forum: Desktop Environments
---

### Post by t0ny on 2006-09-02
I dont know what I did but apt-get and all the gui package managers dont seems to see any thing new. apt-get update goes fine and when I try to do a apt-get upate I get this 
> tony@tony-desktop:/etc/apt$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


The gui update manager does nothing just gray. I click reload and it still nothing.

And here is my /etc/apt/sources.list

> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main universe restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
# deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
# deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main
# deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

# deb [http://itp.tugraz.at/Comp/debian/dists/sarge/desktop/](http://itp.tugraz.at/Comp/debian/dists/sarge/desktop/) binary-i386

# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

# deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
# deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
# deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

# deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
# deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
# deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main
# deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main

Thanks for the help.
](*,)

---

### Post by Jussi Kukkonen on 2006-09-02
Doesn't sound surprising: dapper-security only gets new packages if security flaws are fixed, and dapper-updates is used mostly only if there is bug that is trivial to fix (I believe the only updates after 6.06.1 so far are fixes for a disappearing-menu issue and a wrong icon).

Check the security announcements ([http://ubuntuforums.org/forumdisplay.php?f=20](http://ubuntuforums.org/forumdisplay.php?f=20)) and see if you have those packages if you want to be sure.

---

### Post by johann_p on 2006-09-02
Exactly my observation -- none of the issues I had with Dapper ever got fixed and even security updates are few and often need quite a long time (needed several days to fix the OpenOffice security flaw we had recently, for example -- much longer than with other distros I use.

---

### Post by t0ny on 2006-09-02
Its not the lack of updates it not seeing any thing new. Its a install from the stamped cd 6.06. I know there should be updates because there was tons on my other pc.

---

### Post by buellman on 2006-09-02
> **t0ny said:**
> Its not the lack of updates it not seeing any thing new. Its a install from the stamped cd 6.06. I know there should be updates because there was tons on my other pc.
Ever thought of uncommenting some of your repos in the sources list? :-)

Greets. Buellman

---

### Post by sdebo on 2006-09-02
What does this mean?

Is there a better (but safe) way to get ubuntu updates?

In my case I wish to update Nautilus since I know Ubuntu 6.06 uses an old version.  Is it safe to update that?  How?

Thanks

---

### Post by fragos on 2006-09-02
Truth is there's always something new but not necessarily stable.  Ubuntu 6.10 will integrate the next round of new things.  Updates are reserved for things that are broken.  New releases give you the latest and greatest.  You may if you wish go to gnomefiles.org and stay on the cutting edge but you will need to compile these yourself.  You may find that there are lots of dependancies you will have to accomodate which may in turn break other things you are using.  If you enjoy experimenting, perhaps you should create another partition and dual boot with Edgy which isn't yet stable.  The dual boot gives you a way to dabble in the newest stuff and still have a stable 6.06 to go back to.

---

### Post by t0ny on 2006-09-02
A lot of the comments are me testing if one of them were causing the problem. At one time they were all uncommented. My laptop when I first installed ubuntu it had more then 100 unupdated packages. Then why would this install from the same cd and not updated have no updates?

---

### Post by sdebo on 2006-09-03
Thanks fragos.
If I ever manage to set up my 6.06 version to work as I would like it to, I will dabble with an experimental install.  As it is I am still having a hard time even getting Linux to print, but that is another story...

---

### Post by Jussi Kukkonen on 2006-09-03
> **t0ny said:**
> A lot of the comments are me testing if one of them were causing the problem. At one time they were all uncommented. My laptop when I first installed ubuntu it had more then 100 unupdated packages. Then why would this install from the same cd and not updated have no updates?

Any problems with sources should be visible when you *apt-get update*... 

Did you check if you had the security updates mentioned in the thread I linked?

---

