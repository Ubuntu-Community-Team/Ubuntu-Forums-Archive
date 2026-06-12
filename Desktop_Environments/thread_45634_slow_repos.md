---
title: "slow repos"
date: 2005-07-01
forum: Desktop Environments
---

### Post by DarkManX4lf on 2005-07-01
i added more repositories like the starte guide says but some of them are REAL sloooooooowwww.....like im downloading at 3700BYTES !!! perscond... whats up with this?

---

### Post by angkor on 2005-07-01
[http://backports.ubuntuforums.org/url.php](http://backports.ubuntuforums.org/url.php)

They're too popular. Try another mirror.

---

### Post by DarkManX4lf on 2005-07-01
i tried the ones from  your link but they give me errors when i run synaptic

---

### Post by bored2k on 2005-07-01
[QUOTE=DarkManX4lf]i tried the ones from  your link but they give me errors when i run synaptic[/QUOTE]
 What errors ?

---

### Post by angkor on 2005-07-01
Was that the verification error, cause I read somewhere that's normal...take a look at the backports forum for more info.

---

### Post by DarkManX4lf on 2005-07-01
i get this error

E: Malformed line 35 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.



and here is my sources.list 

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) 
deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/)
deb [http://acm.cs.umn.edu/ubp/](http://acm.cs.umn.edu/ubp/) 



the original backports and the regular links from the starter guide were fine like early yesterday...

---

### Post by DarkManX4lf on 2005-07-01
bump

---

### Post by DarkManX4lf on 2005-07-01
so i reinstalled ubuntu and during the install it had to download some openoffice things...and it was downloading at teh same speed there

---

### Post by bw32 on 2005-07-01
use the defaul repos

---

### Post by DarkManX4lf on 2005-07-01
[QUOTE=bw32]use the defaul repos[/QUOTE]
 that doesnt help either, it is still slow.

---

### Post by manicka on 2005-07-01
How is your networking setup? Are you using DHCP?

Setting up your connection manually may improve things

---

### Post by DarkManX4lf on 2005-07-01
my network connection is fine i think, it was working a day ago and then all of a sudden its REAL slow, but how do i setup my network ?


i really dont think its my network from other sites i can download at 600kb/s

---

### Post by DarkManX4lf on 2005-07-01
this is sad i currently have 6hours remaining to download 26package upgrades, is this only happening to me or do you guys notice it too ?

---

### Post by DarkManX4lf on 2005-07-01
is this happening to anyone else?

---

### Post by DarkManX4lf on 2005-07-02
so its only me ?

---

### Post by angkor on 2005-07-02
No problem here

---

### Post by DarkManX4lf on 2005-07-02
then apt must really hate me then :(

but really tho what could be the problem ? i checked my network and its fine i download at my cap from other sites....

---

### Post by DarkManX4lf on 2005-07-02
ok so then i decided to fully format and reinstall ubuntu and the same problem occurs........maybe its because i used apt too much ?

---

### Post by DarkManX4lf on 2005-07-02
ok, can someone go to this link 

[http://archive.ubuntu.com/ubuntu/pool/main/b/bzip2/](http://archive.ubuntu.com/ubuntu/pool/main/b/bzip2/)

and try to download anything from there and see how fast you get it ?

when i run synaptic that is one of the locations it downloads a package from and i get anything from there at like 3800B/s....

---

### Post by DarkManX4lf on 2005-07-02
anyone ?

---

### Post by locohijo on 2005-07-02
> 
and try to download anything from there and see how fast you get it ?

downloaded a couple of files there the highest i got was at 67kb/s on my end before the files were done

---

### Post by brossiter on 2005-07-02
Same here - currently downloading a package at 3367 B/s from the multiverse, ouch.  Problem started all of a sudden two days ago, haven't touched etc/apt/sources.list in ages.

---

### Post by DarkManX4lf on 2005-07-03
[QUOTE=brossiter]Same here - currently downloading a package at 3367 B/s from the multiverse, ouch.  Problem started all of a sudden two days ago, haven't touched etc/apt/sources.list in ages.[/QUOTE]



this is weird and terribly annoying....i hope it gets fixed.

---

