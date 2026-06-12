---
title: "I did sudo apt-get install kde and kde is not to be seen anywhere"
date: 2006-08-24
forum: Desktop Environments
---

### Post by pranav on 2006-08-24
Hello friends,

I did > sudo apt-get update

sudo apt-get install kde

on an absolutely fresh install of Ubuntu. The only changes i had made was to use > sudo pppoeconf to connect to the internet and had added the universe and multiverse repos from Software properties. 

It downloaded some 236 mb archives and installed it (which took 5 hours on my slow connection). I restarted my PC and I didn't see KDE as an option in the session. 

What have I missed? This is an absolute fresh copy of Ubuntu and I want it to really last for a long-time. I intend to keep this as my most stable distro installed. And I admire both GNOME as well as KDE. and hence i need both. Please tell me what do i do to make kde work ?

---

### Post by asplode on 2006-08-24
you should try this instead

```
sudo aptitude install kubuntu-desktop
```

---

### Post by pranav on 2006-08-24
Thank you for your really quick reply. I posted the query. I went for lunch, came back and there was ur reply. UBUNTU FORUM ROCKS 100% for a reason.


WOW that is another 123 MB of Packages to be downloaded. Shall take me another 120-150 mins to complete the downloading of packages. Shall let you know how it worked out.

---

### Post by JoshHendo on 2006-08-24
That should work. If you hadn't downloaded KDE, you would have to download more for the kubuntu-desktop package.

When it is installed, just select KDE from the sessions when you go to login :)

- Josh

---

### Post by pranav on 2006-08-24
so the correct procedure would have been to type 

> sudo apt-get install kubuntu-desktop

from the very beginning?

what about the XUbuntu environment ?

should i be doing > sudo apt-get install xubuntu-desktop ?

---

### Post by pranav on 2006-08-24
OH...

I made a mistake i typed > sudo apt-get install kubuntu-desktop

instead of the recommended > sudo aptitude install kubuntu-desktop

Sorry.. My mistake.. Now what can be done ?

Can I still do > sudo aptitude install kubuntu-desktop

Please help... i should have paid more attention... really sorry.

---

### Post by padre999 on 2006-08-24
It should be added that it is better to use aptitude instead of apt-get if you install kubuntu-desktop or xubuntu-desktop. Because if you don't like your new desktop you can simply uninstall the packages with all its dependencies and you are back to the system state where you were before. That is not possible with apt-get (or synaptic etc.)
To use aptitude you simply can run
```
sudo aptitude
```
and use the gui to (un)install the packages. Alternatively you can also use it as a command line tool just as apt-get.

---

### Post by FuriousLettuce on 2006-08-24
Aptitude & apt-get do similar things. The difference is that aptitude will remove all unused dependencies when you uninstall a package, whereas apt-get won't.

If I remember correctly, kubuntu-desktop is a metapackage [it doesn't actually contain any files, it simply lists all the dependencies needed to run kubuntu]. This means that if you want to uninstall kubuntu-desktop, doing sudo apt-get remove kubuntu-desktop will only remove the meta-package [which will be a few kilobytes at most] rather than the files themselves. Had you used aptitude and then decided to remove it, aptitude would have gotten rid of the other 125MB of files you downloaded along with the metapackage.

Unfortunately, having used apt-get to download kubuntu-desktop, you can't use aptitude to remove it. It's only really a problem if you are bothered about keeping your installation very clean, or you need the extra hard drive space.

---

### Post by pranav on 2006-08-24
Thank you for explaining the difference between apt-get and aptitude. I am learning.

Also my isp has this crazy policy of disconnecting and connecting the internet connection every 2 hours (so that the p2p users lose connection with their peers). And hence a couple of packages couldn't be installed namely.. kbruch and kcontrol..

what should be done to get them?


what happens if an apt-get or an aptitude download gets disturbed? Is the process resumed ?

---

### Post by masnevets on 2006-08-24
You should be able to just manually apt-get install those interrupted packages. I did a quick test with interrupting downloads on purpose, and it looks like it should resume.

---

### Post by skyttan on 2008-02-26
Thanks for this tread! I too want to install and try KDE on my Ubuntu system.

Thanks,
skyttan

---

