---
title: "Fedora vs. Ubuntu"
date: 2006-07-30
forum: Desktop Environments
---

### Post by roflcopter_1 on 2006-07-30
So... I was wondering if anyone here has tried a recent version of fedora. I took this "linux distro chooser" thing ([http://www.zegeniestudios.net/ldc/index.php](http://www.zegeniestudios.net/ldc/index.php)) and it recommended it first.(Not that I take that too seriously). I was just wondering what is different between it and ubuntu. I'm kinda looking for something a little more "hands-on" than ubuntu. Also, why does Fedora have 5 cd's?

Thanks for your help. I realize this is kinda like rooting for the browns in cincinnati or something like that, but any help is appreciated.

---

### Post by bluevoodoo1 on 2006-07-30
I used Fedora Core 5 for a bit with VMWare. It's a big install, hence the 5 CDs (though I used the DVD install). If I remember correctly VMWare suggested 8 gigs for the install. 

I didn't like the package manager from FC5 as it was quite slow compared to Ubuntu's Synaptic (even under VMWare). Other than that it was a pretty positive experience. 

I also don't know how their support compares to these forums...

If you want something more hands on there's always Gentoo.

---

### Post by Holzster on 2006-07-30
ROFL...

Here is my opinion on Ubuntu & Fedora.

First there are both great - but I like Ubuntu because "it just works" Fedora always to me seems to be right past the stable line in the bleeding edge of updates.  I would do somehting & it would not work.  Little stuff like that.

It has 5 CD's becasue the extra CD's has the software on it that with Ubuntu you grab by downloading it.  Like SUSE it is shipped with everything & the kitchen sink.

This is my opinion I do not want to start a war here Fedora is a great but I just prefer Ubuntu.

---

### Post by Rondonjin on 2006-07-30
> **roflcopter_1 said:**
> So... I was wondering if anyone here has tried a recent version of fedora. I took this "linux distro chooser" thing ([http://www.zegeniestudios.net/ldc/index.php](http://www.zegeniestudios.net/ldc/index.php)) and it recommended it first.(Not that I take that too seriously). I was just wondering what is different between it and ubuntu. I'm kinda looking for something a little more "hands-on" than ubuntu. Also, why does Fedora have 5 cd's?

Thanks for your help. I realize this is kinda like rooting for the browns in cincinnati or something like that, but any help is appreciated.

I just took that test for fun and it said Ubuntu, Debian and Fedora in that order :D I'm actually running Fedora right now although I did dabble with Ubuntu when it was released. I had a couple of problems with Ubuntu, namely, 2 apps would not start but there seems to a fix for that now and I run an English system with Japanese input support but the DBCS fonts were terrible, even after messing around with the config I couldn't get them to display as nicely as they do out of the box in Fedora. There are some packages missing in Fedora that are available for Ubuntu, QDVDAuthor is one and Listen Music Player has to be compiled for FC5 but is available for 6.06. One thing missing from Ubuntu is the Gnome Display utility. On my laptop with a 2.5Mb video card I had to manually edit Xorg.conf to change from 24bit to 16bit video where on Fedora there's a GUI tool for that. I can't understand why Ubuntu take it for granted that everyone is running the latest and greatest video cards, even my main machine only has 8Mb video memory!

Apart from that, there's not much to choose between them, the both have their good and bad points. FC5 is using Gnome 2.14.2 where I think Ubuntu still uses 2.14.1 (maybe with some 2.14.2 fixes?)

Ubuntu does a simple install from one CD and everything else you need, like extra software and languages has to be installed over the net where FC5 has everything and the kitchen sink on the 5 CDs, although you may not use them all in an install.

Hope this helps.

Wayne

---

### Post by teyster2 on 2006-07-30
Fedora is an excellant o/s.  Used 4 without much difficulty except for obtaining video play back and audio, etc.  That's why I like Ubuntu and automatix.  I have recently tried Blag50000.  Based on Fedora, uses RPM's, but is much like Ubuntu in that it uses Synaptic as the package manager and it already has the codecs built in for audio and video.  It would be a great o/s to expand on.  You can get it here if you're interested [http://blagblagblag.org](http://blagblagblag.org).  I have had to cut my experimentations down as the step-daughter and grandkids are around alot taking up my time and my computer.

---

### Post by catlett on 2006-07-30
The ultimate "hands on" distro is Gentoo [http://www.gentoo.org/](http://www.gentoo.org/) (at least in my opinion. you compile and setup everything. nothing is loaded by default. meaning your kernel, kernel modules, sound driver, x window system etc)
A distro that is s "little" more hands on than Ubuntu is Debian (Ubuntu is based on debian) [http://www.debian.org/](http://www.debian.org/)
If you do not know anything about linux, Fedora and Ubuntu are going to look very similar. That is because the window managers are the same. They both use Gnome. 
Most distros look alike. There are 2 main window managers, Gnome and KDE. All the larger distros have one of the two as the default. So if you just look at them they look the same.
They are the same in the beginning and at the end. The kernel is the same linux kernel and the window manager is the same (gnome or kde). The difference is the middle. How the system runs, how the system installs packages and updates. In ubuntu apt is used. In amother yum is used, another uses portage and emerge. That is the big difference and that is usually where people make their choice of distro.
I believe apt is the best. For me aptitude and wget is as good as it gets. Others would disagree and say portage is best etc.
The only way to know what you will like is to try them. But just so you know, Ubuntu is as powerfull as any linux distro and can do anything the others can. You are not locked into defaults. Remember Ubuntu is a modified Sid.
Just try them and eventually you will like one over the other. But for a system that can be installed and used right away for most people's computer needs, Ubuntu with the Automatix script is as good as it gets. In under an hour you will have a system that can do everything an average user wants, with the capability to expand into anything.

---

### Post by Jucato on 2006-07-30
Hmm... seems like nobody mentioned the most obvious difference between the two: Fedora Core uses RPM (RedHat Package Manager) for it's package management, while Ubuntu uses DEB/Dpkg (Debian Package). Beneath the hood, these two handles packages and dependencies differently. But that shouldn't concern new users that much. Let's just say that it's quite a different thing from  what you're used to in Ubuntu.

As for default installations: Fedora Core's installation allows you to decide which set of packages you want to install. It's a more thorough and flexible installation. Ubuntu, on the other hand, has already its own set of default applications, and is more rigid in this sense, but also simpler and easier (at least for the Desktop CD). If you want not having to connect to the internet just to install some more packages, Fedora Core might be for you. If, however, you are mostly satisfied with the defaults, Ubuntu might be a more convenient option.

Fedora Core does NOT need a minimum 8GB to install. Like any other Linux system, the basic default install requires only 3GB ([http://fedora.redhat.com/docs/fedora-install-guide-en/fc5/sn-before-begin.html#sn-installing-storage-configurations)](http://fedora.redhat.com/docs/fedora-install-guide-en/fc5/sn-before-begin.html#sn-installing-storage-configurations)). VMWare Server is configured to suggest 8GB with any installation, whether it be Ubuntu, Fedora Core, or Windows XP. It doesn't adjust itself.

I haven't run Fedora Core that long yet and only on VMWare. So apart from those initial/installation differences, I'm also a bit clueless. :D

---

### Post by Mindflux on 2006-07-30
> **catlett said:**
> The ultimate "hands on" distro is Gentoo [http://www.gentoo.org/](http://www.gentoo.org/) (at least in my opinion. you compile and setup everything. nothing is loaded by default. meaning your kernel, kernel modules, sound driver, x window system etc)
A distro that is s "little" more hands on than Ubuntu is Debian (Ubuntu is based on debian) [http://www.debian.org/](http://www.debian.org/)

where's my laugh hysterically icon?

[http://funroll-loops.org/](http://funroll-loops.org/)

I used gentoo way way wayyyyyyyy way back. Yeah, it's neat.  It's cool to compile your bootstrap et-al. Ultimately compiling packages and whatnot gets old-as-dirt.  This is coming from a veteran FreeBSD user.

While I love FreeBSD deeply, I moved away for the sake of time usage.  I now use debian/etch.   Although I may give slackware another go started with Slackware back at 4.0, stopped in the 9.x range.

I've evaluated so many distro's over the years it's just nilly willy.

---

### Post by bluevoodoo1 on 2006-07-30
> **Fenyx said:**
> Fedora Core does NOT need a minimum 8GB to install. Like any other Linux system, the basic default install requires only 3GB ([http://fedora.redhat.com/docs/fedora-install-guide-en/fc5/sn-before-begin.html#sn-installing-storage-configurations)](http://fedora.redhat.com/docs/fedora-install-guide-en/fc5/sn-before-begin.html#sn-installing-storage-configurations)). VMWare Server is configured to suggest 8GB with any installation, whether it be Ubuntu, Fedora Core, or Windows XP. It doesn't adjust itself.

For some reason, it would not install when I had it set to use 4 gigs. I tried it on two different occasions. Only when I caved and chose the 8 did it work. But perhaps that's just with VMWare.

> It doesn't adjust itself.
Eh... That's not true. It does adjust itself. It suggests 16 gigs for Vista and for me, Vista wouldn't install correctly when I set it to 10 gigs.

---

### Post by Jucato on 2006-07-30
> **bluevoodoo1 said:**
> For some reason, it would not install when I had it set to use 4 gigs. I tried it on two different occasions. Only when I caved and chose the 8 did it work. But perhaps that's just with VMWare.


Eh... That's not true. It does adjust itself. It suggests 16 gigs for Vista and for me, Vista wouldn't install correctly when I set it to 10 gigs.

I haven't tried to install Vista. But KNOPPIX, Fedora Core, Ubuntu, and XP all default to 8GB. Probably it's controlled by some setting in VMWare.

> A desktop system with the default applications requires at least 3 GB of storage.

What they probably mean is the most basic desktop install with no other features except the most basic applications and default choices.

---

