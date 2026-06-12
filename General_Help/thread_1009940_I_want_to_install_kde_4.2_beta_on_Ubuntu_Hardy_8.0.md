---
title: "I want to install kde 4.2 beta on Ubuntu Hardy 8.04"
date: 2008-12-13
forum: General Help
---

### Post by bimaljr on 2008-12-13
Hi

I want to try KDE 4.2 on Ubuntu 8.04 Hardy. Please provide me info how to install.

I am already using KDE 3.5.10

**Update :** I am inspired after seeing this page : [http://arstechnica.com/news.ars/post/20081202-hands-on-kde-4-2-beta-1.html](http://arstechnica.com/news.ars/post/20081202-hands-on-kde-4-2-beta-1.html)

Thank you

---

### Post by maestrobwh1 on 2008-12-13
[https://launchpad.net/~kubuntu-members-kde4/+archive](https://launchpad.net/~kubuntu-members-kde4/+archive)

then use the pulldown for the 'hardy' archive.  Actually you could just copy what is there and paste it as one of your repos and just change "intrepid" to "hardy"

At any rate, this is what you will add through adept-manager, synaptic, or just manually edit /etc/apt/sources.list :

deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main

then install packages kubuntu-kde4-desktop gtk-qt-engine-kde4 kdeplasma-addons

I assume you know what you are doing at this point but after adding those repos, the easiest thing to do would be to open konsole and type:

> sudo apt-get update && sudo apt-get install kubuntu-kde4-desktop gtk-qt-engine-kde4 kdeplasma-addons


It should work well.  I had it running for a while but upgraded to intrepid for other reasons.  If you are running an intel 945GMA video card, post back.  All sorts of hell broke lose because there is a bug with the intel driver and the 945GMA and this card and installing kde4 brought it out.  There was a workaround for me.  On my laptop, I never had an issue because it uses a different graphics card.

KDE4 is 'lighter' in some ways and the newest version seems faster than the old KDE3

---

### Post by bimaljr on 2008-12-13
There is only KDE 4.1.2 for install
But I want to install KDE 4.2 Beta version

---

### Post by maestrobwh1 on 2008-12-13
Oh, duh on me:-) I really need to pay attention.

---

### Post by bimaljr on 2008-12-15
Anyone.. Please help me..

---

### Post by kleeman on 2008-12-15
I have not tried it but........

[http://www.cyberciti.biz/faq/ubuntu-linux-install-kde-42/](http://www.cyberciti.biz/faq/ubuntu-linux-install-kde-42/)

BTW google is your friend :p

---

### Post by bimaljr on 2008-12-22
> **kleeman said:**
> I have not tried it but........

[http://www.cyberciti.biz/faq/ubuntu-linux-install-kde-42/](http://www.cyberciti.biz/faq/ubuntu-linux-install-kde-42/)

BTW google is your friend :p

I tried it but still getting KDE 4.1

---

### Post by Bankai56 on 2008-12-28
:popcorn:
I love this theme!:lolflag:
Anzbodz know how to get the beta in 4.1 firefox and all ubuntu 8.04 stuff looks like crap *sorry to say that* but kubuntu looks great any help or does anyone where to get 4.2?
THX:popcorn:

---

### Post by lenzoid on 2009-02-05
Build it from sources if you can't live without it. The hype around 4.2 is not worth it. It's just a little less buggy than 4.1. KDE 3.5 is the best, most reliable DE you can get at the moment.

---

### Post by scouser73 on 2009-02-06
Visit this site: **[http://www.kde.org/download/#v4.2]("http://www.kde.org/download/#v4.2")**

---

### Post by Farmer of Bricks on 2009-02-06
> **kleeman said:**
> 
[http://www.cyberciti.biz/faq/ubuntu-linux-install-kde-42/](http://www.cyberciti.biz/faq/ubuntu-linux-install-kde-42/)

> **scouser73 said:**
> Visit this site: ][http://www.kde.org/download/#v4.2]("http://www.kde.org/download/#v4.2")


These are instructions for how to install in *Intrepid*, not *Hardy*. 
Sorry if I sound rude, but other than building from source, is there a way to install in *Hardy*?

---

### Post by kleeman on 2009-02-06
> **Farmer of Bricks said:**
> These are instructions for how to install in *Intrepid*, not *Hardy*. 
Sorry if I sound rude, but other than building from source, is there a way to install in *Hardy*?
Try following the directions but replace every instance of "intrepid" with "hardy"

I checked the repo site and it is set up for hardy as well as intrepid and gutsy

---

### Post by Syock on 2009-02-13
> **kleeman said:**
> Try following the directions but replace every instance of "intrepid" with "hardy"

I checked the repo site and it is set up for hardy as well as intrepid and gutsy

Then you have checked wrong. If you checked [https://launchpad.net/~kubuntu-experimental/+archive/ppa?field.name_filter=&field.status_filter=published&field.series_filter=hardy](https://launchpad.net/~kubuntu-experimental/+archive/ppa?field.name_filter=&field.status_filter=published&field.series_filter=hardy) you'll find that only 3 packages for hardy are on that repo.

And not even project-neon has the hardy packages maintained. It seems they were all removed.
If you understand how all the dependecies work, you can install kde4.2 from the kubuntu-experimental's intrepid repo (of course, ubuntu's intrepid repo also need to be enabled), but then expect some kde3 apps to be removed due to conflict of packages.

---

### Post by hg21 on 2009-02-13
This site was very helpful for me to go to 4.2.  I think the instructions could be adapted to 8.04.

[http://www.ubuntugeek.com/how-to-install-kde-42-beta-in-ubuntu-810-intrepid-ibex.html/](http://www.ubuntugeek.com/how-to-install-kde-42-beta-in-ubuntu-810-intrepid-ibex.html/)

It's well worthwhile going to 4.2 it's a vast improvement on 4.1

---

### Post by kleeman on 2009-02-14
> **Syock said:**
> Then you have checked wrong. If you checked [https://launchpad.net/~kubuntu-experimental/+archive/ppa?field.name_filter=&field.status_filter=published&field.series_filter=hardy](https://launchpad.net/~kubuntu-experimental/+archive/ppa?field.name_filter=&field.status_filter=published&field.series_filter=hardy) you'll find that only 3 packages for hardy are on that repo.

And not even project-neon has the hardy packages maintained. It seems they were all removed.
If you understand how all the dependecies work, you can install kde4.2 from the kubuntu-experimental's intrepid repo (of course, ubuntu's intrepid repo also need to be enabled), but then expect some kde3 apps to be removed due to conflict of packages.
You are correct I didn't look closely enough.

My suggestion is that if you want to use kde 4 you upgrade to intrepid. If you don't wish to do this because of stability issues then stick with kde 3.5 which after all is much more stable than any of the kde 4s. 

There are limits to the flexibility of linux guys :)

---

### Post by R33D3M33R on 2009-02-23
In the repositories of Hardy there is a highly unstable 4.0.5, some packages are already up to 4.1.2, but its ridiculous that a LTS release doesn't have more stable KDE 4.2 in the repos.

---

