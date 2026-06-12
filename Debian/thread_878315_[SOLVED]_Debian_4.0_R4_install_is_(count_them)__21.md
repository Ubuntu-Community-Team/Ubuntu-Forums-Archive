---
title: "[SOLVED] Debian 4.0 R4 install is (count them)  21 .iso CD's??"
date: 2008-08-02
forum: Debian
---

### Post by rated727 on 2008-08-02
After more than 15 years of Micorsoft (only) experience, I am investigating some of the Linux distros and was shocked to find ... (see thread title) ... I **MUST** be missing something!!

Linux offers **so** many choices and subtleties.  I am trying a few until I find something that I want to stay.  

My installation is to be a dual-boot (Linux/WinXP) box on a (three computer) peer network.  The second is a WinXP laptop and third is (OS not yet determined) print/peripheral server. -and it all lives behind a Linux firewall box-


So why is it ...?
 
Ubuntu Linux - - one .iso CD (currently installed)
Mist Linux - - one .iso CD
Berry Linux - - one .iso CD
Damn Small Linux - - (it certainly is)
Gentoo Linux - - one .iso CD (so far, untried)
Windows XP Pro - - one CD 
Debian Linux - - O.M.G.

OK, I'm sure that the 21 CD's (plus 5 more for updates) includes all source code and a library full of documentation, but do I have to burn all 26 to install on a system??

How much disk space is required? Certainly it is less than the 2.46 Terabyte that many CD's might suggest (I exaggerate)

Network installation ... If the information of 26 CD's is trafficed during the installation does it finish in less than one week? ... two?

What are minimum system requirements for a fair (even if slow) test?
- - 766 mHz P3, 256 mb RAM, 20 gb hdd available in my current test box (AKA "The Crash Can")

Thanks for answers, advice and input.

---

### Post by scragar on 2008-08-02
huh, 3 DVDs or 21 CDs, intresting...

A quick check of the docs confirms that only the first disk need be burnt, the remaining disks can stay on a HD and the installer can work from the images.

Doesn't sound very user freindly though... I think the idea of 21 disks is that it contains a lot of programs in the repo's that your unlikly to use.

---

### Post by mauud777 on 2008-08-02
You can install debian from the first dvd

---

### Post by liquidfunk on 2008-08-02
Just grab the Netinst CD and use the internet to grab the rest of the stuff you need. 30-45mins install time, depending on your internet of course. 

 All the latest packages.

---

### Post by p_quarles on 2008-08-02
The full set is only required if you don't happen to have a reliable net connection. If you do, the netinstall CD (120 MBs or so) image is the preferred option for installation. Extremely flexible and -- unless you are scared off by the ncurses interface -- very easy to use.

---

### Post by rated727 on 2008-08-02
Installation via network connecition is not necessarily a problem, but I know that for every other of the Linux distros that I have tried, I have experimented with various options on each of several attempts.  As example, I've installed Ubuntu onto at least 3 differant partition configurations and among those I have used various locations for installing GRUB.

It doesn't seem fair to tie up as much bandwidth as is required for an installation when I am likely to do it more than once. Please consider, Long experience with MS Windows sometimes leads me to experiment with things that a lesser experienced computer user wouldn't dream to try ... with unpredictable (and often disasterous) results.

Thanks mauud777 - - 1 DVD is well within the limits of reason, certainly better than the 3 + update at debian.org
Thanks also to all others.

Does anyone have comments about minimum hardware requirements? 
... for a reasonable test installation?
... for reasonable continued use.

I wouldn't want to run Ubuntu or WinXP on my test box as a 'permanent' installation.  But I could get an idea of the "look and feel" of either OS on that box. (as I have already done with Mint 5, Berry, DSL)

---

### Post by basenvironment on 2008-08-03
> **rated727 said:**
> 
OK, I'm sure that the 21 CD's (plus 5 more for updates) includes all source code and a library full of documentation, but do I have to burn all 26 to install on a system??
Uh actually I think those are all binary ISOs the source ISOs are separate. The update disks are to update previous versions TO r4. You can burn as little or as much as you want. CD1 provides a good default system, the netinst provides a good base install to build on, and the bizcard as a tiny system that will download everything.

> 
How much disk space is required? 
Depends on what you install 
> 
Network installation ... If the information of 26 CD's is trafficed during the installation does it finish in less than one week? A netinst doesnt take long at all. 
> 
What are minimum system requirements for a fair (even if slow) test?
- - 766 mHz P3, 256 mb RAM, 20 gb hdd available in my current test box (AKA "The Crash Can")
Nothing wrong with that system, a little low on memory maybe. It will simply depend on what you install on it.

---

### Post by Vorian Grey on 2008-08-03
It will install a base system with working GUI with the first CD. You can apt-get the rest. I've done it several times.  I think those other CD's and DVD's are for people who have poor internet connections. They contain common programs that people use that are in the repository and their source code.

---

### Post by Erik Trybom on 2008-08-04
Do these 21 CDs cover the entire Etch main repository?

---

### Post by Bachstelze on 2008-08-04
> **Erik Trybom said:**
> Do these 21 CDs cover the entire Etch main repository?

Yes.

---

### Post by huxterby on 2008-08-06
> **mauud777 said:**
> You can install debian from the first dvd

Ditto, I was going to say the same. You would probably need about 10 CD's if you downloaded the Ubuntu repos as well.

The netinstall cd is a nice option if you have a router setup. Just install the base (130 MB) then add your chosen apps and Desktop Environment.

I always go for Xfce personally.

Huxterby

---

### Post by utUtu on 2008-08-06
> **rated727 said:**
> After more than 15 years of Micorsoft (only) experience, I am investigating some of the Linux distros and was shocked to find ... (see thread title) ... I **MUST** be missing something!!

Linux offers **so** many choices and subtleties.  I am trying a few until I find something that I want to stay.  

My installation is to be a dual-boot (Linux/WinXP) box on a (three computer) peer network.  The second is a WinXP laptop and third is (OS not yet determined) print/peripheral server. -and it all lives behind a Linux firewall box-


So why is it ...?
 
Ubuntu Linux - - one .iso CD (currently installed)
Mist Linux - - one .iso CD
Berry Linux - - one .iso CD
Damn Small Linux - - (it certainly is)
Gentoo Linux - - one .iso CD (so far, untried)
Windows XP Pro - - one CD 
Debian Linux - - O.M.G.

OK, I'm sure that the 21 CD's (plus 5 more for updates) includes all source code and a library full of documentation, but do I have to burn all 26 to install on a system??

How much disk space is required? Certainly it is less than the 2.46 Terabyte that many CD's might suggest (I exaggerate)

Network installation ... If the information of 26 CD's is trafficed during the installation does it finish in less than one week? ... two?

What are minimum system requirements for a fair (even if slow) test?
- - 766 mHz P3, 256 mb RAM, 20 gb hdd available in my current test box (AKA "The Crash Can")

Thanks for answers, advice and input.

Instead of counting the number of Cd's, and bothered to read first the FAQ or Getting Debian, you would be amazed you just need about 7.5MB for the amd64 installer.

---

### Post by doorknob60 on 2008-08-25
You can install a full working installation complete with Gnome (or another DE if you download the cd1-kde or cd1-xfce discs instead) with just the first CD (no need for DVD) and you don't need an internet connection while installing it either. I've done it like that many times.

---

