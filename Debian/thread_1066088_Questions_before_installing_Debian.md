---
title: "Questions before installing Debian"
date: 2009-02-10
forum: Debian
---

### Post by Jollyollydog66 on 2009-02-10
So I've been using Linux for about six months now originally starting out with Ubuntu, then Kubuntu, with several other distro's (Fedora, OpenSUSE, Dreamwalk, Xubuntu) in between and I've had Zenwalk on my laptop for about three months now. I really like Debian based distros and I've been thinking of just full on switching to Debian. I just have a couple questions. 

I can't log onto my college internet until I'm able to open a browser is that going to be an issue with downloading? 
Do you have to download the full 13g of discs? It's not an issue so much as a choice of whether to order the discs or download. It would take about two weeks to download on my college internet lol. 
Is there any information I should find out before attempting to install? I intend on reading some wiki's and how to's but any other info is helpful. I'm also going to attempt a vmare installation before the actual one. 

The reason I'm looking at Debian is because I want to fully configure an OS for my system and I've liked and had good luck with Debian based OS's. I feel like most distros come with a large amount of extra packages and they feel very bloated. I'm not a big fan of the Slackware package system, and the Debian community is really great.

---

### Post by zcecc22 on 2009-02-10
> I can't log onto my college internet until I'm able to open a browser is that going to be an issue with downloading? 

I would say that if you are able to use apt without opening a browser first on any debian based system, you should nt have any problem doing a net install (about 150 mb instead of the full cd set).

Otherwise, you could still install a text web client, log in on your web portal and then apt-get the rest of the system.

If that does nt suit you, the final way is to use a livecd such as the standard ubuntu disc, and simply debootstrap the system. It invovles a fair amount of manual configuration but gives you a lot of control.

---

### Post by Jollyollydog66 on 2009-02-10
I definetly can't get online until I have access to a web browser. The text based one sounds like it could work but I've never used one before. The Live CD sounds very doable.

Downloading the first dvd now and I'm going to see how it goes... though I have 39 hours before it finishes.

---

### Post by jay576 on 2009-02-10
If you need to login to the university internet every boot you may need to install a browser of sometype just to login to the campus internet in order to download packages.  This said you should be able to get by with just a terminal based web browser.

Debian has a lot of different ways to install, you won't need the whole cd collection but the netinstall cd may not work for you.

---

### Post by Hallvor on 2009-02-11
Like stated above, there are many ways to install Debian. Even though you have the option to download several dvds or 21(?) CDs, you only need CD 1 or DVD 1 to install your system. You even get a graphical installer if you want to.

If you want to configure your system from ground and up, I`d suggest a netinstall, but even the vanilla installs with many applications do not feel bloated at all. I installed Debian on a spare computer, an old Dell Optiplex with 1,5 ghz processor and 512 MB RAM. On a clean KDE desktop with all the software installed, it uses less than 70 MB of RAM. It boots and shuts down faster than my 2,4 ghz computer with 1024 MB RAM running PCLinuxOS, and that distro certainly isn`t a slug compared to Kubuntu and many other KDE distros.

---

### Post by Jollyollydog66 on 2009-02-12
Alright I've installed Debian in a virtualbox and I havn't had any problems. Got Java and flash to work really fast. Nevermind that last sentence managed to get sound to work with a simple click on virtualbox.

I ended up downloading the first cd and using that to install. Though I have internet connection through virtualbox anyways I wanted to make sure it would work without internet.

---

