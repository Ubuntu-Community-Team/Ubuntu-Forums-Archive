---
title: "Please help me install KDE 4.2 w/o fubar'ing everything..."
date: 2009-02-25
forum: Desktop Environments
---

### Post by brjoon1021 on 2009-02-25
I have Intrepid with Gnome installed. I want to have both Gnome and KDE as login options.   I put the following PPA in my sources.lst and imported the key.  deb [http://ppa.launchpad.net/kubuntu-experimental/ubuntu](http://ppa.launchpad.net/kubuntu-experimental/ubuntu) intrepid main   I am ready for sage advice...   Thanks, B

---

### Post by x33a on 2009-02-25
kde 4.2 has been added to intrepid backports, so i don't think you need the new repository.

to install kde 4.2
```
sudo aptitude install kubuntu-desktop
```

---

### Post by brjoon1021 on 2009-02-27
I even have PPA repos enabled and the latest version availabe is 4.1.4

[http://ppa.launchpad.net/kubuntu-experimental/ubuntu](http://ppa.launchpad.net/kubuntu-experimental/ubuntu)

[http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu)

How can I get 4.2 ?

---

### Post by jackgu1988 on 2009-03-01
you need to uncomment some lines in your /etc/apt/sources.list

for me it's lines 39, 40, 46 and 47

so all you need to do is:
```

sudo gedit /etc/apt/sources.list
```

and then uncomment the lines (remove the # in the front) so it looks something like this:
> 
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

then you do ```
sudo apt-get update
sudo apt-get install kde kde-core kubuntu-desktop
```

---

### Post by jastonas on 2009-03-08
Thank you Jackgu.. i ve seen the same guide somewhere on a different website. Can you explain what the difference is from adding the sources from launchpad? Do they contain the same version packages? And another thing..
Adding the launchpad repos worked perfectly fine for me, trying to do it the way you said i met some difficulties. My sources.list did not contain this line
```
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
```
so uncommenting it would be a paradox.. since it doesnt not exist.. :p
Adding it though made everything fine. That was just a little note to complete this guide...

---

### Post by jackgu1988 on 2009-03-08
> **brjoon1021 said:**
> I even have PPA repos enabled and the latest version availabe is 4.1.4

[http://ppa.launchpad.net/kubuntu-experimental/ubuntu](http://ppa.launchpad.net/kubuntu-experimental/ubuntu)

[http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu)

How can I get 4.2 ?

as you see jastonas, brjoon1021 had a problem installing kde 4.2 even after adding the launchpad links and so did i. so i suggest a different solution that worked for me. if your sources.list does not contain the lines i suggested you to uncomment you can simply copy and paste them from my post if launchpad doesn't work.

---

### Post by jastonas on 2009-03-08
Ofcourse and that is exactly what i suggested.. i already told you i added the lines and ofcourse it works. Brjoon1021 had a problem because he did not add the correct repos.
for anyone interested, these are the launchpad repos for kde 4.2
```
http://ppa.launchpad.net/project-neon/ubuntu intrepid main
```

I still dont know what the difference is.

Even though juacgu's way seems more "trustworthy" the strange thing is that when searching google for kde 4.2 ubuntu i always get the launchpad solution.

---

