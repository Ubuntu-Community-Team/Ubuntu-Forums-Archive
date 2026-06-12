---
title: "sadly dissapointed"
date: 2006-08-17
forum: Desktop Environments
---

### Post by barfy on 2006-08-17
seems that this build is rather unstable and for most non linux users to complicated to maintain what a shame. I have a desire to learn but this OS needs to be debugged more. no offence meant, but this acts like the "Beta of VISTA" with failing "JAVA" and low conectivity to the internet, can't say it's user frendly, no not at all!! been fighting with the build for two days with no ability to access forum or any other form of support.finaly had to reinstall XP just to make this posting. that dissapoints me even more!! I hate XP!! the biggest security issue on the net today! can't see any viable solutions posted on my delemma so I'll just have to try another destro. that saddens me greatly since I've been installing "hedgehog" since it's release.(I do @ 12 installs a month) and found ubuntu to be supported better then any M$ OS. since I have a very limited knowledge of linux (seems I have no problem installing various destros of it)and no knowledge of command line whatsoever, I am in a quandry of which destro to use for learning on. was hopeing that ubuntu would do it but that dosen't appear to be the case.  I'll keep watching the builds of this destro,waiting for my turn to be on the ubuntu bandwagon.but till then I'll keep looking elswhere for a learnable destro. sorry guys but "dapper" gets a big thumbs down from this guy!!!:frown: :frown:

---

### Post by Tomosaur on 2006-08-17
Maybe you should tell us your problem? Sounds like net connection issues, there are hundreds of threads about those, I'm confident at least one will help you out.

---

### Post by -ko- on 2006-08-17
About the user friendly part, maybe you just don't like your desktop environment. 

I dont like gnome either and therefore desided to choose for Kubuntu, with KDE, and not gnome. Since I installed this distribution 2 weeks ago, I have'nt boot Windows more then one time to finish something that really had to be done in Windows.

Installing KDE @ Ubuntu isn't that hard.

```
sudo apt-get install kubuntu-desktop
```

You'll be rid of gnome with the following command:

```
sudo apt-get remove ubuntu-desktop
```

hopefully, you like KDE better then gnome. There will be a fix for your internet troubles to, but i cant think of one right now. Please supply us more information and we'll see how we can help you :)

---

### Post by barfy on 2006-08-17
seems that after installing using the OEM install makeing my configs then deleate the temp account the java scripting fails in the firefox browser.  opened the java counsel in firefox and seen many soft-wrap errors plus some line errors.this occured on almost every site I visited Except the Ubuntu home page. no access to any forums no access to e-mail sites either so I couldn't post a request on this forum since I needed to create an account first. (rock and a hard place)tried eraseing the HD and do a fresh install but the results were the same. normaly on a windows system I would uninstall firefox and do a fresh install after a scan-disk and defrag this would clean up the problem but since there is no scan-disk or defrag on linux that was not an option plus you can't uninstall and reinstall firefox without losing "Yelp" and "Gnome-desktop" and a couple of other packages which remove the add&remove programs option.(I did try though as you can probably tell)could not load a second browser in the second build(claimed that I needed to fix broken packages first?)this was a install from the alt install disk CPU was running at a normal 3-4% with the system idle but ram was running 192mgbs out of 256 consistantly with 77(?)active processes (hate to use the term Bloatware in this cercumstance since I have no idea what the basic running leavels are for this build)but this could not run after install if I went by the minimums posted at the download site (32Mgbs ram)most of the systems I build start out with only 128MGB ram witch make this destro unuseable to me for buildings systems for sale!

---

### Post by Tomosaur on 2006-08-17
High RAM usage is the norm in Linux - since RAM not being used is wasted RAM. Your programs run more efficiently because of this.

Anyway, the alternate install CD is designed for people who know what they're doing in linux. It is primarly intended for servers. The Java problem is a common one, and yes, it's very irritating. You should download the official SUN Java runtime environment and plugins rather than rely on Ubuntu to have it set up for you.

You may benefit from using a 'post-install' script such as EasyUbuntu or Automatix, which should help get your system up and running in no time at all.

You could also enable the commercial repositories and download Opera. I too had problems with Firefox initially, but I've got them sorted now.

---

### Post by JordanSPE on 2006-08-17
Barfy,

I think your experience with this distro is isolated.  Ubuntu has proved for many an excellent distro for familiarizing yourself with a Linux environment, and tends to have some very full featured and powerful apps available through it's repositories, and a very quick learning curve.  What are some of the problems you seem to be having, maybe some of us in this thread can help you out.  The network connectivity issues could be a driver issue.

What kind of connection are you using, is it wireless?  I have found that on my laptop, sometimes i get spotty wireless connectivity, but that is the only issue I have had.  I am relatively new to Ubuntu and Linux, and was very surprised by how easy it was to get the hang of.  If I did have an issue, the community support always proved phenomenal.  Hope some people around here can help you, giving up Ubuntu would be giving up a great OS.

JordanSPE

---

### Post by shoagun on 2006-08-17
It's too bad to hear this.  I've always thought that the number one most promising thing about Dapper Drake is the ease of installation.  I highly suggest you use the normal live CD to install instead of the alternative CD.    Once you get it installed, it's true that it will probably take a bit of work to get it all working like you want, but you should be able to immediately come to the forums, and they will definitely help you.

---

### Post by JordanSPE on 2006-08-17
Like recommended in another post, I utilized Automatix ([www.getautomatix.com](www.getautomatix.com)) when I was first getting everything set up.  It is an excellent little application, that installs a lot of the codecs and software needed to make a system really usable.  I would highly recommend it.  Before it was recommended to me in another forum, i was having serious issues with getting things to work as well, namely multimedia.

-JordanSPE

---

### Post by barfy on 2006-08-17
thanks for the head-up on the ram! but as to using the alt disk most of the systems I build are equiped with only the basic CD drive small HD and 128 Mgb ram, processors range from 450-1gig. as to advanced users I have been installing linux in systems for 3 years without any incident or failures (suse,slackware,ubuntu,alt linux,pc linux os,knoppix,fedora and a few of the off brands as well)and have never had this issue before. guess thats what happens when you do somthing for yourself. (LOL) might have to give the latest suse build a whirl since I used it for about a month with no issues whatsoever,but it still feels like a windows product to me so maybe I'm just to picky!(lol)

---

### Post by cevans on 2006-08-17
> **barfy said:**
> normaly on a windows system I would uninstall firefox and do a fresh install after a scan-disk and defrag this would clean up the problem but since there is no scan-disk or defrag on linux that was not an option plus you can't uninstall and reinstall firefox without losing "Yelp" and "Gnome-desktop" and a couple of other packages which remove the add&remove programs option.(I did try though as you can probably tell)could not load a second browser in the second build(claimed that I needed to fix broken packages first?)

In a terminal, you can use 'sudo apt-get install --reinstall package' to reinstall a program, or 'sudo dpkg -r --force-all package' and 'sudo dpkg -i --force-all package' to remove and add the package whle ignoring dependencies.

---

### Post by shoagun on 2006-08-17
> **barfy said:**
> thanks for the head-up on the ram! but as to using the alt disk most of the systems I build are equiped with only the basic CD drive small HD and 128 Mgb ram, processors range from 450-1gig. 

Maybe try [Xubuntu]("http://www.xubuntu.org/")

---

### Post by barfy on 2006-08-17
never heard of Xubuntu whats the difference?

---

### Post by shoagun on 2006-08-17
I haven't used Xubuntu.  But it is a "lightweight" version of Ubuntu made specifically for low end systems.  I've heard good things about it.  Though, even with the basic machine you describe, shouldn't the normal Ubuntu (installed from the live CD) work?

---

### Post by barfy on 2006-08-18
seems like my problem is not with the install, alt disk recognizes all my hardware and all drivers seem to work fine. just have the issue with java. perhaps I should build an off line machine to learn on first and then once I get the hang of the OS then put it online. since I place the OS into machines that I sell, perhaps some one should place the minimum requiered specs. on the download sites for all the ubuntu builds,thanks for the heads-up on xbuntu since I have wondered what to install on some of the real old systems I rebuild. do all the builds come with the OEM install? this alone is a great feature witch should be in all linux builds. seems as though ubuntu is the first to add this feature giving it the one-up on all the rest. I also think that some of the more common problems could be better solved if someone were to place all the termanal commands that solve the basic issues into a PDF or text doc. and include them with the build. this would make it a bit easyer for newbies to solve their issues with a simple copy/paste rather then spend their day searching through this site.maybe something like winmechanic would be a good idea as well. a simple one button fix would a great boon for those of us who are not proficiant in the command line yet. but since that hasn't been thought of yet I and the rest of us newbies will just have to muddle through with the manual and lots of trial and error. LOL

---

### Post by shoagun on 2006-08-18
This site helped me out a lot when I first started with Ubuntu
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

It's funny, I feel like I've had every firefox plugin related problem out there, but I never had an issue with Java.  Try downloading Java from here.  The file you'll get is executable.  It will take you through a step by step installation (like a set-up file in windows).  If there are questions you don't know the answer to, you can probably just hit enter, because the defaults are all probably correct. 
[http://www.java.com/en/download/index.jsp](http://www.java.com/en/download/index.jsp)

Good luck!

---

### Post by shoagun on 2006-08-18
These instructions fro installing Java are helpful

[http://www.java.com/en/download/help/5000010500.xml#download](http://www.java.com/en/download/help/5000010500.xml#download)

---

