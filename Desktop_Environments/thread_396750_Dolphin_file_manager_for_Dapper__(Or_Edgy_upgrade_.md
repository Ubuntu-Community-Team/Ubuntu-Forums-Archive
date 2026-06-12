---
title: "Dolphin file manager for Dapper?  (Or Edgy upgrade?  Or...?)"
date: 2007-03-29
forum: Desktop Environments
---

### Post by Phrawm48 on 2007-03-29
It would appear, based on my exploration of the repositories, Web, and this forum, that the Dolphin file manager is not compatible with the Dapper (6.06) release of Ubuntu.

Is this in fact true?

If it is true, is there a relatively painless way to upgrade a happily tweaked and well-running Ubuntu-Kubuntu Dapper system to a version (Edgy?  Even later?) that supports Dolphin?

Cheers & thanks,
Ric
SFO

---

### Post by kerry_s on 2007-03-29
I don't think it's true, make sure all your repos are on and do a search in synaptic(command line> sudo apt-get install dolphin) it's in universe.
If you can't find it> [http://digilander.libero.it/dr_kabuto/dapper/dolphin_0.6.1-2_i386.deb](http://digilander.libero.it/dr_kabuto/dapper/dolphin_0.6.1-2_i386.deb)
It's not the latest, but it is the version built for dapper.

---

### Post by Phrawm48 on 2007-03-30
Thanks, I downloaded the package but am hesitant to install it outside of Synaptic.

At the same time, Dolphin isn't showing up in the repositories I have (line numbers added):

```

1  ## Uncomment the following two lines to fetch updated software from the network
2  deb-src http://archive.ubuntu.com/ubuntu dapper main restricted
3
4  ## Uncomment the following two lines to fetch major bug fix updates produced
5  ## after the final release of the distribution.
6  deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
7  deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted
8
9  ## Uncomment the following two lines to add software from the 'universe'
10  ## repository.
11  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
12  ## team, and may not be under a free licence. Please satisfy yourself as to
13  ## your rights to use the software. Also, please note that software in
14  ## universe WILL NOT receive any review or updates from the Ubuntu security
15  ## team.
16  deb-src http://archive.ubuntu.com/ubuntu dapper universe
17
18  deb http://security.ubuntu.com/ubuntu dapper-security main restricted
19  deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
20
21  deb http://security.ubuntu.com/ubuntu dapper-security universe
22  deb-src http://security.ubuntu.com/ubuntu dapper-security universe
23
24  deb http://archive.ubuntu.com/ubuntu/ dapper multiverse universe main restricted
25  deb-src http://archive.ubuntu.com/ubuntu dapper multiverse
26
27  deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
28
29  deb http://archive.canonical.com/ubuntu dapper-commercial main
30
31  ## Add Wine repository.  RB, 2007-03-27
32  deb http://wine.sourceforge.net/apt binary/

```I've tried adding repos but this always seems to break stuff so that I have to clear out *sources.list* and start over.

So I may have to wait a while to sort this out...

Cheers & thanks 'gain,
Ric
SFO

---

### Post by kerry_s on 2007-03-30
That's a deb it will be in synaptic when you install. Just double click on the deb to install, gdebi will open up and check that the package is installable it will say "all dependency's satisfied" if it's okay, if not it will tell you what is missing or that it can't be installed.

---

### Post by Phrawm48 on 2007-03-30
Thanks but 'twould appear that the Dapper gods don't want me to install Dolphin.  Double-clicking *dolphin_0.6.1-2_i386.deb*  opened the Package Installer which then displayed the following mesage:

[B][COLOR=Red]Error: Dependency is not satisfiable: kdelibs4c2a
[/COLOR][/B]
I'm abandoning this for now.  Some number of days or weeks from now, when I'm smarter, I'll make another attempt...

Thanks again for your help!
Ric
SFO

---

### Post by kerry_s on 2007-03-30
Oh well, you gave it a shot.

---

