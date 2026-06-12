---
title: "differences between the different flavors of ubuntu?"
date: 2013-06-17
forum: Desktop Environments
---

### Post by BigZ1981 on 2013-06-17
Hi guys.  I recently installed kubuntu at the suggestion of someone on these forums due to the crashing issues I had when trying to install standard ubuntu.  Now I'm also seeing all these other flavors.  I want to know what the pros & cons of each are and if I should dip my foot into another flavor like xubuntu, maybe trying LinuxMint, but I'm at an impasse with my limited knowledge of Linux.  I tried Fedora, but I had too many issues trying to get it set up...I can't remember what it was, but I had to abandon that option. I know LinuxMint & Fedora are only touching the tip of the iceberg since I've heard of Slackware & Archlinux, etc...  Not that I don't love the world of possibilities that I now have with kubuntu, but now that I've delved into something I've only lightly dabbled in a few times, and enjoying the experience, I want to see what other options I have and see if I want to work in a different environment.

---

### Post by cincinnatus13 on 2013-06-18
An OS and desktop environment (DE) are completely different things.
If you want the feel of a different DE, you can do it all within Ubuntu for the most part.
sudo apt-get install lubuntu-desktop
xubuntu-desktop
gnome-shell
etc. 

If you want, you can try Cinnamon (what Mint uses) or MATE (also what Mint uses), E17 (what Bodhi uses), etc.
A quick search will tell you exactly how to install but most are just a simple command to fetch it from Ubuntu repos. Others might need a PPA added (latest Cinnamon, Enlightenment (E17) etc.)

If you need to uninstall later- [http://www.psychocats.net/ubuntucat/pure-ubuntu-13-04/](http://www.psychocats.net/ubuntucat/pure-ubuntu-13-04/)

---

### Post by dave2001 on 2013-06-18
> **BigZ1981 said:**
> Hi guys.  I recently installed kubuntu at the suggestion of someone on these forums due to the crashing issues I had when trying to install standard ubuntu.

Welcome to Ubuntu! 

Kubuntu: If stability is something you're looking for, kubuntu might not be the best choice. It's a great flavor, one of my two favorites, but it does have occasional issues with applications crashing. It's also not an "officially canonical supported" derivative anymore. Has great eye-candy if you want it, and great productivity features.

Xubuntu: I love Xubuntu, it strikes a great balance between utility, speed, and looks. It runs smoothly as well. It comes with a nice light default application load-out, but you can always add more! It's an official ubuntu dirivative, so it should be consistent for some time to come.
 
Lubuntu: Uses a very lightweight and simple desktop. It's great for older computers that need the small footprint, or for people who like a really clean, austere look.

Ubuntu Gnome: Has the Gnome3 desktop, which is a full-featured and resource intensive environment. Some people have criticized both Gnome3 and Unity for "hiding" a lot of the operating system from the user.

I'm one of those people who really dislikes Unity. I think it's slow, cumbersome, and obfuscated, so I'm not recommending "standard" Ubuntu to anyone anymore.

Fedora is similar to Ubuntu Gnome. LinuxMint is a lot like the older "classic" ubuntu desktop, which a lot people liked.

ArchLinux and Slackware can take a bit more "linux know-how" than the others mentioned, but they also offer thier own advantages. The 'Buntu family is deffinitely the most new-user friendly of the linux bunch.

---

### Post by whatthefunk on 2013-06-18
> **dave2001 said:**
> 
Kubuntu: If stability is something you're looking for, kubuntu might not be the best choice. It's a great flavor, one of my two favorites, but it does have occasional issues with applications crashing. It's also not an "officially canonical supported" derivative anymore. Has great eye-candy if you want it, and great productivity features.

Kubuntu is very, very stable.  far more stable than any Ubuntu install Ive used.  Also, it is an official derivative.  It used to have a special status and receive funding from Ubuntu for development, but that no longer happens.  It has the same status now as the other flavors.

To the OP, the Ubuntu flavors are: Lubuntu, Kubuntu, Xubuntu, Edubuntu, Ubuntu GNOME, Mythbuntu, and Ubuntu Studio.  You can read more about them here: [http://www.ubuntu.com/about/about-ubuntu/derivatives](http://www.ubuntu.com/about/about-ubuntu/derivatives)

Slackware, Fedora, Arch and Mint are other varieties of Linux.  Mint is based on Ubuntu so has a lot in common with it.  The other distributions you mentioned are on the other side of Linux (not based on Debian) so many things like package management are much different.  Check this chart out:  [http://linuxhere.files.wordpress.com/2010/08/lintimeline1.png](http://linuxhere.files.wordpress.com/2010/08/lintimeline1.png)

---

### Post by BigZ1981 on 2013-06-18
I like that timeline chart.  I remember a time when I was trying to dabble and decide among Mandrake, Red Hat, or SuSE.  I was able to get Mandrake going somewhat with the KDE environment, but there were no drivers for my NIC.  I didn't like Red Hat, and I got fed up before trying SuSE.  Now, I'm just so fed up with Windows, and like the idea of designing my desktop (multiple VDs, rather) to my liking.  kubuntu has been pretty stable for me.  I have had few minor program crashes, but also wish everything was available in repository.  I'd much prefer to run my linux-based programs as opposed to using Wine, but for some things, it's a necessary evil.

Okay, so maybe I should elaborate my question a bit better.  I'm familiar with the fact that you have different flavors/OSes, and then there are different DEs.  So what's the run down among the different DEs?  KDE, GNOME, LXDE, XFCE.  Also, I saw Ubuntu Studio.  I have periods where I will do heavy graphics, video, and/or audio work.  What's the scoop on it?  My questions are more to do with what your experience is with it and also if I should just stay with kubuntu & the apps are all available in repository?

---

### Post by BigZ1981 on 2013-06-18
> **cincinnatus13 said:**
> An OS and desktop environment (DE) are completely different things.
If you want the feel of a different DE, you can do it all within Ubuntu for the most part.
sudo apt-get install lubuntu-desktop
xubuntu-desktop
gnome-shell
etc. 

If you want, you can try Cinnamon (what Mint uses) or MATE (also what Mint uses), E17 (what Bodhi uses), etc.
A quick search will tell you exactly how to install but most are just a simple command to fetch it from Ubuntu repos. Others might need a PPA added (latest Cinnamon, Enlightenment (E17) etc.)

If you need to uninstall later- [http://www.psychocats.net/ubuntucat/pure-ubuntu-13-04/](http://www.psychocats.net/ubuntucat/pure-ubuntu-13-04/)

OK so now my question is this, should I install another DE via terminal, will I need to use the uninstall command, or can I leave it as is & will I be able to switch between DEs?

---

### Post by malspa on 2013-06-18
> **BigZ1981 said:**
> OK so now my question is this, should I install another DE via terminal, will I need to use the uninstall command, or can I leave it as is & will I be able to switch between DEs?

You can leave the other DE installed, and you can switch between DEs at the log-in screen.

Well, I've done this a lot of times in the past, but these days when it comes to DEs like KDE, GNOME, and Xfce, I prefer to keep things separate. So, for example, right now I have both Ubuntu and Kubuntu installed, on separate computers actually. Of course, you could always just run other version from a live disk (or flash drive, as the case may be), or in a VM, if you just want to take a look and check things out.

---

### Post by whatthefunk on 2013-06-18
> **BigZ1981 said:**
> Okay, so maybe I should elaborate my question a bit better.  I'm familiar with the fact that you have different flavors/OSes, and then there are different DEs.  So what's the run down among the different DEs?  KDE, GNOME, LXDE, XFCE.  Also, I saw Ubuntu Studio.  I have periods where I will do heavy graphics, video, and/or audio work.  What's the scoop on it?  My questions are more to do with what your experience is with it and also if I should just stay with kubuntu & the apps are all available in repository?

In order to fully appreciate them, I think youll have to try yourself.  Ive only used KDE and LXDE.  My main desktop uses KDE and I love it.  It has thousands of configuration options and is ideal if you want to customize.  Also, KDE programs are some of the best out there.  Amarok, K3b, Ktorrent and Ksnapshot are some of the best programs out the in my opinion.  You can run these in other DEs but youll have to pull in huge amounts of KDE libraries and you wont get the integration between the programs that you would get in a full KDE install.  KDE eye candy is also great, if youre into that sort of thing.  

LXDE is great if you have an older, low spec computer.  It gives you a traditional desktop with a fair amount of customization options.  I used to use it on my old laptop until I discovered Crunchbang.

---

### Post by cincinnatus13 on 2013-06-18
[http://www.renewablepcs.com/about-linux/kde-gnome-or-xfce](http://www.renewablepcs.com/about-linux/kde-gnome-or-xfce)

Posted by TNFrank the other day. I was looking for it but didn't find it until today. That gives you a basic rundown.
But I also agree that you may as well just try them. No harm and nowadays, real easy to get rid of if you want to.

---

### Post by BigZ1981 on 2013-06-18
okay, I'm installing gnome-shell & I'm at a page that's asking me about display managers...gdm or lightdm, which should I pick?

---

### Post by cincinnatus13 on 2013-06-19
All it is saying is what you want your login screen to look like. Basically lightdm is what you're using now and gdm is what Gnome natively uses (basically shows the time and notifications and then you slide it up to reveal your user name on a blank grey screen.)
You can search google for an image of gdm. Nothing special but it works for me.
It really doesn't matter one way or another though as you pick whatever session you want when you log in.

---

### Post by BigZ1981 on 2013-06-19
OK.  I stuck with lightdm, but now I can't even load gnome de.  On xfce de now and playing with it.  It's pretty different & is taking some getting used to.

---

