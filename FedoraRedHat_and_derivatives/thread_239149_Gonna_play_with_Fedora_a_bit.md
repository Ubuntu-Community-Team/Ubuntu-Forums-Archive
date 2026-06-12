---
title: "Gonna play with Fedora a bit"
date: 2006-08-18
forum: Fedora/RedHat and derivatives
---

### Post by jdong on 2006-08-18
Need to test my dual-core setup, a new release of VMWare server, beta Azureus, and also the latest Fedora experience.

So, what better way to do all of the above than torrenting a Fedora Core 5 respin DVD and firing up vmware?

---

### Post by ComplexNumber on 2006-08-26
**jdong**
how are you finding fedora so far?

---

### Post by jdong on 2006-08-26
Overall, I had a positive experience with Fedora. It has a very polished desktop, simple administration, good balance of technology, responsive updates, fairly complete and up-to-date repositories, and a large community.


If I really wanted to nit-pick, I guess I could build up a list of complaints about Fedora. Please take these lightly -- they're just things I found 'irritating', but I can make just as big (if not bigger) of a list for Ubuntu or any other distro :)


* Lack of proprietary/3rd party drivers. Ubuntu (and several other distros) go that extra mile to build up as comprehensive hardware support as possible. This means either bundling or making easily accessible drivers that are not built into the kernel (Both open source, like rt2500, and not, like ipw3945/nvidia/fglrx/atheros). All of my wireless cards require drivers not in Fedora's default install, and it's a real PITA to get networking set up.

* Too many updates. After installing the respin, I had around 150 updates to install. In a week, there were 50 more updates. Now, fortunately I have a broadband connection and obsessive-compulsive updating disorder (why else would I have started Backports? ;) ), but I can easily see how people can be irritated by all these updates.

* Repositories not as comprehensive as Ubuntu/Debian's. Fedora Extras has come a long way since RH9/FC1, but it's still not as comprehensive as Ubuntu's Universe. There are too many times where I have to reach out to an RPM locating service to find packages I want, and even times when I find myself building RPM's.

* Yum is still considerably slower and less intelligent than APT. I got to say, Yum has made impressive improvements over its first introduction, but overall it's still slower to work with than APT, and on two occasions in my testing I encountered a case where it was unable to process a dependency (both were during updates in 3rd party repos), where I had to manually help yum resolve some dependencies before it'd continue.


Anyway, overall if you're lucky enough to have a system fully supported by official kernel drivers, or don't mind a bit of extra work every time you reinstall or get a kernel update, Fedora is a great distribution and is definitely worth a look at. For me, I will continue to be a [k]ubuntu user.

---

### Post by Omnios on 2006-08-26
I have a Fedora Partition so I am try booting with XP/Ubuntu/Fedora. Fedora seems realy nice and polished but found the package manager and updater took extreemly long to time and I mean extreemly long to look at packages.

---

### Post by jdong on 2006-08-26
Yum gets faster over time. I'm not gonna pretend like I know how Yum works internally, but then again I will :)

APT downloads a package index called "Packages.gz" or Packages.bz2 that contains all the information about every package in the repository. Yum downloads a repodata.gz file that only contains a list of all the packages in a repository. Therefore, the initial download is faster with Yum. However, for each package Yum considers, it must then download a package header with more info about dependencies, etc. As a result, if there's 150 updates, it has to download 150 of these headers. That takes time.

---

### Post by Iandefor on 2006-08-27
Informative, unless you just pulled that out of your *** :-P.

---

### Post by ComplexNumber on 2006-08-27
**jdong**
before i set myself up with a wireless card, i would often go [here]("http://rpm.pbone.net/") to dwnload individual packages and them burnt them all to disk. its still agreat and comprehensive plcae to download individual packages, if necessary.

> 

* Yum is still considerably slower and less intelligent than APT. I got to say, Yum has made impressive improvements over its first introduction, but overall it's still slower to work with than APT, and on two occasions in my testing I encountered a case where it was unable to process a dependency (both were during updates in 3rd party repos), where I had to manually help yum resolve some dependencies before it'd continue. you can download apt for fedora. its in the repos. if you want to use a gui, use Smart version 0.42 because fast, very stable, and has lots of support for adding other repos. i would recommend that you additionally use livna([http://mirror.atrpms.net/livna/fedora/5/i386/](http://mirror.atrpms.net/livna/fedora/5/i386/)) and  atrpms([http://dl.atrpms.net/fc5-i386/atrpms/stable]("http://dl.atrpms.net/fc5-i386/atrpms/stable%29"))[]("http://dl.atrpms.net/fc5-i386/atrpms/stable%29").

---

### Post by jdong on 2006-08-27
Yes, but again, that's a bit of inconvenience.... I absolutely hate setting up networking. I expect my system to have access to the network/internet out of the box :)


Anyway, as I prefaced my rant earlier, just silly things I complain about. :)

---

### Post by ComplexNumber on 2006-08-27
> **jdong said:**
> Yes, but again, that's a bit of inconvenience.... I absolutely hate setting up networking. I expect my system to have access to the network/internet out of the box :)


Anyway, as I prefaced my rant earlier, just silly things I complain about. :)
it does do networking out of the box....almost ;). i had to juggle my partitions about recently, so i had to do a few reinstalls. i found that if i added wifi-radar and the ndiswrapper packages, i could literally have wifi up and running within 10 minutes after i'd installed the distro. there was no setting up of the wifi card at all because either network manager and/or wifi-radar had configured it all correctly without any effort by me.

---

### Post by heffo_j on 2006-08-28
I used FC4 for a long time and liked it a lot. I changed to Ubuntu after the upgrade to FC5 mucked everything up. I have looked at FC5 using vmware server and it seems to have settled down a lot since I downloaded it the first time. There is a lot of *.rpm stuff that runs out of the box. My second favourite gnome os. My favourite KDE is Mepis (used it too for a while).

Regards
John

---

### Post by baldy1324 on 2006-09-01
its much like mac os x and everything is perfect and stable but yum is really slow and not as good package selection even with fedora extras.

---

