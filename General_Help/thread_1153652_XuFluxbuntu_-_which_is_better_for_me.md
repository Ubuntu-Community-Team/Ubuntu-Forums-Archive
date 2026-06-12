---
title: "Xu/Fluxbuntu - which is better for me?"
date: 2009-05-09
forum: General Help
---

### Post by DnDer on 2009-05-09
The system is old: trying to dual-boot a 98SE machine. Belarc tells me I'm looking at a 500mhz P3 with 384 megs of memory. Graphics card is NVIDIA RIVA TNT, the report also tells me.

I have little to no command line experience, so Flux worries me. But Xu is heavier on the resources, right (?), on such an old computer, I worry about the load on it.

The old box is really a workhorse. I do plenty of chatting on it, along with some p2p (not as much anymore) and plenty of internet surfing and limited streaming media viewed. The tradeoff between performance and usability - will it be that big? For a machine that's not going to be working too hard (don't expect I'll ever need Gimp or Scribus or anything like that on here), which is really the better -buntu?

I was given Flux 7.10 and Xu 8.04... probably won't be able to pick a different version than that till I get some distro up and running. (98SE needs to be DBAN'd before I work on it anymore. It's gotten too ugly to work with.)

TIA, guys!

---

### Post by monsterstack on 2009-05-09
I loaded Xubuntu on to my laptop last year, with its 800Mhz of raw Powah, and it was noticeably clunky. I expect you will have a similar experience.

I went ahead and stripped down a generic Ubuntu install and ended up running Openbox with the Gnome-panel, which made a lot of difference. All the little tweaks I made are basically included in [Crunchbang Linux]("http://crunchbanglinux.org/") [crunchbanglinux.org]. 

Or if you want to do it yourself, you can follow this excellent [Openbox guide]("http://urukrama.wordpress.com/openbox-guide/") [wordpress.com], on urukrama's blog.

---

### Post by Yellow Pasque on 2009-05-09
I'd recommend you install Xu 8.04 and see how it runs. 

This might interest you:
[http://ubuntuforums.org/showthread.php?t=1133123](http://ubuntuforums.org/showthread.php?t=1133123)

---

### Post by DnDer on 2009-05-09
I'm reading now.

Yea, I'm at 384 mb and the motherboard is maxed on what it can handle. I need to make as tiny a footprint as possible. I'll see if the topic has tips on that, inside their debates.

---

### Post by kerry_s on 2009-05-09
base install + window manager + just the programs you need

is the best way to get a truly light system, most prefabs are made to cover a wide range of people, so all though there called light there loaded.
you might also want to consider going with a faster base system, such as arch or debian.

i use arch linux on 450mhz 256mb ram, i rarely drop into swap on my install.

---

### Post by kerry_s on 2009-05-09
my bag i missed the part where you only have 2 disks to choose from.
go with the xubuntu 8, the other 1 is not supported anymore and you won't have repos to grab programs from.

---

### Post by binbash on 2009-05-09
Fluxbox is lighter than xfce, so i would stick with fluxbox with that box.

---

### Post by snowpine on 2009-05-09
Well, Fluxbuntu 7.10 is no longer supported, so that's out of the question. Xubuntu should be okay on that hardware, but maybe a little slow. You can always install Fluxbox on top of an Xubuntu install to speed things up.

I second the recommendation for Crunchbang; it is sort of the "new Fluxbuntu" in my opinion.

---

### Post by kerry_s on 2009-05-09
well he just wants to get a system on there to work with, once he has a install he should download and burn a cd for something lighter.
it's up to him though he might just be happy with xubuntu, being he is just getting started in linux and does not know his way around yet.

---

### Post by DnDer on 2009-05-09
I'll try Xubuntu, then, and see how it runs. Because I am just starting out, most of the other thread goes over my head, except for some of the broader generalities.

For example, how does installing fluxbox (another distro) on top of xubuntu make the computer faster? Adding more, on a lightweight system should make it worse, no?

---

### Post by bodhi.zazen on 2009-05-09
Part of the issue is window managers vs desktop environments.

To be honest, all the window managers are fairly light.

[http://xwinman.org/](http://xwinman.org/)

It is not the window manager that slows you down, it is the services and default applications.

Xubuntu is more a desktop environment, but it is not, IMO, a light weight installation.

See this thread for ideas on light weight distros :

[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

To be honest. I prefer the Slackware based distros - Wolvix, Zenwalk, or Slax.

---

### Post by snowpine on 2009-05-09
> **DnDer said:**
> I'll try Xubuntu, then, and see how it runs. Because I am just starting out, most of the other thread goes over my head, except for some of the broader generalities.

For example, how does installing fluxbox (another distro) on top of xubuntu make the computer faster? Adding more, on a lightweight system should make it worse, no?

Both Fluxbuntu and Xubuntu have Ubuntu as their core system. The difference is the graphical user interface (known as a desktop environment or windows manager). If you start with Xubuntu (Ubuntu+Xfce)and then add Fluxbox, you basically end up with Fluxbuntu (Ubuntu+Fluxbox). You could even choose between Xfce and Fluxbox each time you log in. It will not slow your computer down to have multiple options installed, just use a tiny bit more hard drive space. 

Frankly, if you are new to Linux, Xfce is a friendlier place to start than Fluxbox, so give Xubuntu a try first and let us know how it goes. :)

---

### Post by bodhi.zazen on 2009-05-09
> **snowpine said:**
> Both Fluxbuntu and Xubuntu have Ubuntu as their core system. The difference is the graphical user interface (known as a desktop environment or windows manager). If you start with Xubuntu (Ubuntu+Xfce)and then add Fluxbox, you basically end up with Fluxbuntu (Ubuntu+Fluxbox). You could even choose between Xfce and Fluxbox each time you log in. It will not slow your computer down to have multiple options installed, just use a tiny bit more hard drive space. 

Frankly, if you are new to Linux, Xfce is a friendlier place to start than Fluxbox, so give Xubuntu a try first and let us know how it goes. :)

What you say is only "skin deep" and only applies to the window manager.

Under the surface Fluxbuntu is NOT Ubuntu + Fluxbox. There are MAJOR differences in package selection and services run at boot.

If you install Ubuntu or Xubuntu + fluxbox you will NOT have Fluxbuntu.

---

### Post by paradigm2 on 2009-05-09
I use fluxbox on my Gentoo box which is 750 Mhz and 640MB RAM.  Its noticeable faster than when I ran Xubuntu (Xfce).

Flux box does take a little gettign used to and you will have to use the terminal to set it up and likely to tweak your menus, but it is pretty much point and click like KDE, Gnome, or Xfce after that.  I am typing this right now over fluxbox and firefox. :)

---

### Post by paradigm2 on 2009-05-09
> **bodhi.zazen said:**
> What you say is only "skin deep" and only applies to the window manager.

Under the surface Fluxbuntu is NOT Ubuntu + Fluxbox. There are MAJOR differences in package selection and services run at boot.

If you install Ubuntu or Xubuntu + fluxbox you will NOT have Fluxbuntu.

Also when I last checked fluxbuntu it seemed to me as if the official release still was on 7.10 (?) and the website seemed to have some issues.
I'd be a little nervous about this...though it would be great if they updated it and fixed things up.

Of course he could do a minimal Ubuntu install and just throw on fluxbox and slim as well. But that's probably not an easy option if one isn't good with the terminal.

---

### Post by bodhi.zazen on 2009-05-09
Xubuntu is not a bare bones install + XFCE .

---

### Post by EV500B on 2009-05-09
(IMHO) The default install of any -buntu version are bloated with so.. many services and software that, it will naturally make your computer slow, especially on some old systems.
Why don't you try to install it minimally using the alternative cd and then install all the/your needed applications using *aptitude*. Your system will be faster than with the default install.

Non *buntu:
If all that you want is a fast distro while using it's default installation, try [AntiX]("http://antix.mepis.org/").
The interface is not that bad, the applications are fairly good (and numerous) and it's fast; Yeah, fast!.
It is a debian-based distro, so... just an *aptitude* or *apt-get *and you're getting your favourite apps up.

---

### Post by DnDer on 2009-05-09
> **EV500B said:**
> (IMHO) The default install of any -buntu version are bloated with so.. many services and software that, it will naturally make your computer slow, especially on some old systems.
Why don't you try to install it minimally using the alternative cd and then install all the/your needed applications using *aptitude*. Your system will be faster than with the default install.

Non *buntu:
If all that you want is a fast distro while using it's default installation, try [AntiX]("http://antix.mepis.org/").
The interface is not that bad, the applications are fairly good (and numerous) and it's fast; Yeah, fast!.
It is a debian-based distro, so... just an *aptitude* or *apt-get *and you're getting your favourite apps up.

Is "minimal install" an iso option to download and burn, or something in an advanced configuration setup from the install? Also, I'm not sure what "aptitude" is, or honestly how to use apt-get. 

I understand some linux theory, but I've not put it into practical application before. For example, I know "apt-get" was explained to me as "download the programs you want without going to the website for it." And I also know as much as "live cd = rescue data from failed windows when it won't boot anymore." That's about the sum total of my linux experience.

There was a teacher who showed us linux and tried to teach how to use chmod when he was discussion permissions in windows vs permissions in linux. But it didn't really stick with me.

So... if something's requiring a lot of terminal to get started? That's not going to happen. Not yet. Half of the other topic I was linked to didn't make a lick of sense to me, and I read almost all 12 pages. I mean... up until about two weeks ago, I thought Red Hat was still a free distro, instead of having been converted to Fedora.

I am *that* behind. =\

---

### Post by snowpine on 2009-05-09
> **bodhi.zazen said:**
> If you install Ubuntu or Xubuntu + fluxbox you will NOT have Fluxbuntu.

I agree with you 100%; Xubuntu 8.04 with Fluxbox is superior to Fluxbuntu 7.10 in every way, which is why I recommended it to the OP. ;) I would never recommend Fluxbuntu 7.10 to a new Linux user, would you?

---

### Post by bodhi.zazen on 2009-05-09
Depends on the user and the computer.

As it so happens, yes I personally know two new users with older hardware both of whom were very happy  with fluxbuntu.

---

### Post by DnDer on 2009-05-09
It's only about a 15 gig hard drive... but even with 98SE, I suppose I could triple boot and try out both options. However, many questions will now follow.

(1) What order do I install them in?
(2) How do I partition? fdisk and then pick install partition? or does *buntu do that on install?
(3) Add fluxbox or leave as xubuntu, since other partition will be fluxbuntu?
(4) How would I even add fluxbox?

That's... just off the top of my head. Sorry I'm pretty slow about this. I'll be happy just once I get some OSs installed... =\

---

### Post by snowpine on 2009-05-09
> **bodhi.zazen said:**
> Depends on the user and the computer.

As it so happens, yes I personally know two new users with older hardware both of whom were very happy  with fluxbuntu.

What about the fact that Fluxbuntu 7.10 has reached its end of life, while Xubuntu 8.04 is supported through 2011? That is the deal-breaker for me as far as recommending Fluxbuntu. Try explaining to someone using Linux for the very first time why they can't update their system or install new applications from the repositories. Fluxbuntu was pretty cool back in '07, but it is a dead distro at this juncture. Check out the forums at [http://community.fluxbuntu.org](http://community.fluxbuntu.org) if you don't believe me.

The OP has only two choices, Fluxbuntu 7.10 and Xubuntu 8.04. Xubuntu has good support from Canonical and on these forums, and won't reach its end of life for two more years. Easy decision.

---

### Post by DnDer on 2009-05-09
Well, the OP is also planning on using 98SE, another unsupported OS that has reached the end of its lifespan. The important thing may not be the ability to get new packages, but to still be able to get old ones that will work.

That being said... Venturing into a new world, having guiding resources available is a very good thing, indeed.

---

### Post by -kg- on 2009-05-09
> **snowpine said:**
> What about the fact that Fluxbuntu 7.10 has reached its end of life, while Xubuntu 8.04 is supported through 2011? 

The OP has only two choices, Fluxbuntu 7.10 and Xubuntu 8.04. Xubuntu has good support from Canonical and on these forums, and won't reach its end of life for two more years.

At this juncture I would have to agree.  However I did go to the Fluxbuntu website just a bit ago, and it seems they are testing an Intrepid version, with a Jaunty version in the "Experimental" stage.  No downloads available on the site, though.

Xubuntu *should* run OK on a computer with your statistics, though it's going to be a bit slow.  Of course, just about *anything* you run on that computer is going to be slow compared to the newer hardware available.  But as long as you're going to do some browsing with (like you said) limited video streaming and the like, it should run at an acceptable speed.

Just don't depend on it for gaming! :P

---

### Post by albinootje on 2009-05-09
> **DnDer said:**
> Belarc tells me I'm looking at a 500mhz P3 with 384 megs of memory. Graphics card is NVIDIA RIVA TNT

I'd use Xubuntu because it's still supported. And in the future you might want to try Crunchbang, read about it, and see screenshots here : [http://crunchbanglinux.org/wiki/about](http://crunchbanglinux.org/wiki/about)

---

### Post by snowpine on 2009-05-09
> **DnDer said:**
> Well, the OP is also planning on using 98SE, another unsupported OS that has reached the end of its lifespan. The important thing may not be the ability to get new packages, but to still be able to get old ones that will work.

That being said... Venturing into a new world, having guiding resources available is a very good thing, indeed.

Sorry for talking about you in the 3rd person. ;)

I have restricted my comments in this thread to Xubuntu vs. Fluxbuntu, because those are the two choices you gave us. My recommendation? Don't limit yourself to those two choices. Try as many Linux distros as you can, and figure out which one speaks to you. It is kind of a rite of passage. :)

---

### Post by DnDer on 2009-05-09
I tried Fedora on a different computer, and I kind of liked it. Didn't really get to explore it much, though.

I ran Heron on my other computer for a while... And while it was nice, it didn't really grab me and shake me. (Maybe because I'm an Opera and Safari user before I tend to resort to Firefox.) It's definitely a neat experience, and was amazingly helpful in recovering a windows OS (someone walked me through the terminal commands).

For whatever reason, I can't get DSL to work on anything. I've burned the image to two different CDs and tried to load it once onto a 512mb memory key I had lying around... and I just couldn't figure out how to make it go - or I'd be using that instead of Flux/Xubuntu, I think.

I looked at Suse, but I'm not sure about it yet. I think it's all the desktop environments that's really throwing me. I have yet to settle into one I really like. I grew up on Windows and fell in love with Mac's Classic and OSX while I was in college studying journalism and radio (media production has always been Mac's forte, so I had to learn it).

So I'm really not sure what I want other than just something that works and something that's lightweight. I'm not terribly well-funded as most of my paychecks go to the staples of survival. Toys and software aren't often high on the list... So the hardware I've got has to last me. That's why I'm trying to breathe life back into my 98SE box with whatever distro will get me back to normal operation the best (office suite, web browsing, chat... really, that's about it - just an ordinary workhorse).

A friend of mine told me to try Slack. He loves it. Tells me it'll be great CLI experience... I'm still trying to pick a distro and learn how linux works before I learn how to manipulate linux.

So, yea, I think I forgot the original question, but that's the reason I'm switching to linux is legacy support, hardware limitations, and financial reasons. I also like building/playing with computers... so new toys (that are free) are always win.

(Also, I wasn't offended you used third person referring to me. I was just wondering if anyone read poster names when they replied. I know I sometimes don't. Good advice is good advice whoever it comes from... I just don't always remember to associate it with a name.)

---

### Post by albinootje on 2009-05-10
> **DnDer said:**
>  A friend of mine told me to try Slack. He loves it. Tells me it'll be great CLI experience


I used to use Slackware years ago, but you'd better try Arch Linux for a good CLI experience, and .. Arch Linux is i686 optimized, and 
with Arch Linux you can make your desktop lighter than e.g. plain Ubuntu... Or is a PII from the i586 family and not i686 ?

---

### Post by Yellow Pasque on 2009-05-10
> Or is a PII from the i586 family and not i686 ?
The OP has a PIII, and both are based on Intel's P6/i686 architecture.
[http://en.wikipedia.org/wiki/Intel_P6](http://en.wikipedia.org/wiki/Intel_P6)

---

### Post by paradigm2 on 2009-05-10
> **DnDer said:**
> 

So I'm really not sure what I want other than just something that works and something that's lightweight. 

You might like this:

[http://www.linuxmint.com/blog/?p=724](http://www.linuxmint.com/blog/?p=724)

> 


The team is proud to announce the release of Linux Mint 6 Fluxbox Community Edition. Linux Mint Fluxbox Community Edition is based on Xubuntu 8.10 Intrepid, Linux 2.6.27, Fluxbox 1.0.0 and Xorg 7.4. Included is an all-new menu system, Mint-FM2, Slim as a display manager, Live CD features that should make it easier to install on low-end machines, a brand new &#8220;Software Manager&#8221;, FTP support in mintUpload, proxy support and history of updates in mintUpdate, mint4win (a Linux Mint installer for Microsoft Windows), and much more minty goodness. For a complete list of new features read: What&#8217;s new in Felicia Fluxbox CE?


> 
Introduction to the Fluxbox Edition:

The Fluxbox Community Edition is built with the emphasis on a lightweight and yet fully functional desktop centered on the Fluxbox window manager. Even though we strive to provide out-of-the-box readiness for all your hardware and common computing tasks, Linux Mint Fluxbox CE is easily configurable to run on lower-spec hardware with the tools needed for doing so readily available.

For a list of know issues and for upgrade instructions, please visit the Release Notes.

System requirements:

    * x86 processor
    * 128 MB of system memory (RAM)
    * 2 GB of disk space for installation
    * VGA graphics card capable of 800×600 resolution
    * CD-ROM drive


If I were in your shoes and didn't want to mess with either the Ubuntu minimal installation w/ fluxbox, gentoo ([http://gentoo.org](http://gentoo.org)), or Arch ([http://www.archlinux.org/](http://www.archlinux.org/)), i'd probably go with the above over fluxbuntu 7.10.

---

### Post by albinootje on 2009-05-10
> **Temüjin said:**
> The OP has a PIII

Thanks for the correction, I got confused after reading another thread about someone with a PII.
> 
and both are based on Intel's P6/i686 architecture.
[http://en.wikipedia.org/wiki/Intel_P6](http://en.wikipedia.org/wiki/Intel_P6)
Thanks for the information, good to know this (and Arch Linux rocks :) ).

---

### Post by DnDer on 2009-05-10
Xubuntu is installed and running. I'm going to give it a few days of workhorsing like I normally do.

I'll let you know how I like it. Thanks for all the suggestions, guys.

---

### Post by ufugu on 2009-05-11
Seconding the Linux Mint Fluxbox CE suggestion.

It's easy to use, lightweight, and it looks nice too.

---

### Post by RedSquirrel on 2009-05-11
The following instructions are helpful for someone who is new to the idea of building up from a minimal Ubuntu:

[http://psychocats.net/ubuntu/minimal](http://psychocats.net/ubuntu/minimal)

By following those instructions, you still get the fancy login screen (gdm) and the **synaptic** package manager, which should make a newcomer feel at least somewhat comfortable. ;)

The tutorial installs icewm, but you can install a different window manager, e.g., fluxbox, or you could install the essential Xfce components via the **xfce4** meta package.

---

