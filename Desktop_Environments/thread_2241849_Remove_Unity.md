---
title: "Remove Unity?"
date: 2014-08-28
forum: Desktop Environments
---

### Post by mlnease on 2014-08-28
Hello,  I'm  a devoted xubuntu/xfce user and wonder if It's safe to remove Unity altogether?  As a DE per se it's of absolutely no use to me and the farther I get from it the better I like it.  Would doing this break dependencies or cause other problems I haven't thought of yet?  Any other reasons not to?    Thanks in advance.

---

### Post by monkeybrain20122 on 2014-08-28
If you use xubuntu why is there Unity in the first place?

---

### Post by ajgreeny on 2014-08-28
Depending on what packages you have installed it is possible that you may have one or two dependencies that are unity linked.

I run Xubuntu 12.04 and as a result of installing grsync (I think), I have two packages with unity in their names, but so what?  I do not like and do not run unity, but it does not worry me that there are those two packages installed, as they do not actually produce any unity "symptoms".

---

### Post by mlnease on 2014-08-28
> **monkeybrain20122 said:**
> If you use xubuntu why is there Unity in the first place?Dunno, MB--it's there without my having installed it so I assume it was included by default when I installed xubuntu.

---

### Post by mlnease on 2014-08-28
> **ajgreeny said:**
> Depending on what packages you have installed it is possible that you may have one or two dependencies that are unity linked.

I run Xubuntu 12.04 and as a result of installing grsync (I think), I have two packages with unity in their names, but so what?  I do not like and do not run unity, but it does not worry me that there are those two packages installed, as they do not actually produce any unity "symptoms".Thanks for the response.  Synaptic shows that I have fifty or sixty packages installed with 'Unity' either in the name or the description--hence my hesitation.

---

### Post by buzzingrobot on 2014-08-29
Packages in the Canonical repos are, obviously, built to run on Ubuntu. Since Unity is the default Ubuntu interface, that means packages will be compiled against Unity libraries, etc. When you install those packages on Xubuntu or any other flavor, the Unity dependencies will also be installed.  

The same kind of thing happens if you install a KDE package on a non-KDE system:  You'll probably also get a very large number of KDE dependencies.

Use of the "--no-install-recommends" option to apt-get can reduce some of that, but hard dependencies remain hard dependencies.

---

### Post by ajgreeny on 2014-08-29
If you have synaptic installed as a package manager try removing those unity packages one by one, just out of interest, to see what else will be removed as well that you know you need, eg in my case, if I try to remove libunity9 it also wants to remove grsync, liferea and usb-creator-gtk with it, all of which I need and will keep.

By doing that you may find some packages that you've added that brought all those unity packages with them.  That is one of the beauties of synaptic; it is so flexible in its uses.

---

### Post by mlnease on 2014-08-29
> **buzzingrobot said:**
> Packages in the Canonical repos are, obviously, built to run on Ubuntu. Since Unity is the default Ubuntu interface, that means packages will be compiled against Unity libraries, etc. When you install those packages on Xubuntu or any other flavor, the Unity dependencies will also be installed.  

The same kind of thing happens if you install a KDE package on a non-KDE system:  You'll probably also get a very large number of KDE dependencies.

Use of the "--no-install-recommends" option to apt-get can reduce some of that, but hard dependencies remain hard dependencies.
Thanks, that all makes sense.  I guess when I first started using Ubuntu (Dapper), GNOME was the default Ubuntu interface and it never occurred to me to want to remove GNOME (or to wonder how many GNOME dependencies I might have).

I suppose the simple answer is that xubuntu is, at this point, probably inseparable from Unity.  I like xubuntu/xfce so well that I'll probably live with that if I must.  

I did a web upgrade from 12.04.? to 14.04.1 that went wonderfully well (after a disastrous attempt to install manually from an ISO DVD).  After another point upgrade or two, I think I'll try a fresh install and experiment with minimizing Unity on that install.

Thanks for the "--no-install-recommends" tip and for your time and attention.

---

### Post by mlnease on 2014-08-29
> **ajgreeny said:**
> If you have synaptic installed as a package manager try removing those unity packages one by one, just out of interest, to see what else will be removed as well that you know you need, eg in my case, if I try to remove libunity9 it also wants to remove grsync, liferea and usb-creator-gtk with it, all of which I need and will keep.

By doing that you may find some packages that you've added that brought all those unity packages with them.  That is one of the beauties of synaptic; it is so flexible in its uses.

Thanks for the excellent suggestion--I'll try monkeying around with that before trying a fresh install.  Would you advise marking in Synaptic for 'Removal' or 'Complete Removal'?

Thanks for your time and attention.

---

### Post by ajgreeny on 2014-08-29
The default removal type in synaptic is for complete removal, I think, though you can check that in the preferences of your synaptic very easily.

I changed that to "Keep configuration" in mine so I now get a chance to keep configs if I want, or remove if I prefer.  It is entirely up to you but can sometimes be useful if you have spent some time configuring an application and need to remove and then reinstall.

Your choice, I'm afraid.

---

### Post by mlnease on 2014-08-29
> **ajgreeny said:**
> The default removal type in synaptic is for complete removal, I think, though you can check that in the preferences of your synaptic very easily.

I changed that to "Keep configuration" in mine so I now get a chance to keep configs if I want, or remove if I prefer.  It is entirely up to you but can sometimes be useful if you have spent some time configuring an application and need to remove and then reinstall.

Your choice, I'm afraid.

Very good--thanks again.

---

### Post by buzzingrobot on 2014-08-29
> **mlnease said:**
> 
I suppose the simple answer is that xubuntu is, at this point, probably inseparable from Unity.

Well, yes and no, but, I think, mostly no.

Apps need to use support libraries to function correctly in any environment, whether that's Unity or Gnome Shell, KDE or XFCE.  Those libraries will be dependencies of those applications. Ubuntu and all the official flavors, as well as many derivatives like Mint, all pull the same applications from the same servers, Apps that have Unity packages as dependencies will brings those in; apps with XFCE dependencies will bring those in, etc., regardless of which environment they're being installed.  

(I once counted about 30 packages in Mint with "unity" in the name.)

It's a result of the way dependencies work. The libraries, etc., may or may not actually be needed in the "foreign" environment.

It works the other way.  If, say, you want to run the MintMenu on your Ubuntu Mate system, you can add the Mint repos and install it.  You will also install a few Mint dependencies and find a new ".linuxmint" folder in your home directory.

There's nothing of the Unity interface -- the Launcher, the Dash, HUD, the scopes and lenses, web apps, etc. -- in Xubuntu. It's possible, by trial and error, to prune some of the Unity dependencies -- I've done it -- but nothing operational changes. You just have a a fewer files on the drives.

---

### Post by vasa1 on 2014-08-29
The developers of some apps now include dependencies to cater to the Unity desktop. I've see this with Lubuntu and posted about it here: [http://ubuntuforums.org/showthread.php?t=2181775](http://ubuntuforums.org/showthread.php?t=2181775)

This will probably grow if Unity gets more popular.

---

### Post by mlnease on 2014-08-29
> **buzzingrobot said:**
> Well, yes and no, but, I think, mostly no.

Apps need to use support libraries to function correctly in any environment, whether that's Unity or Gnome Shell, KDE or XFCE.  Those libraries will be dependencies of those applications. Ubuntu and all the official flavors, as well as many derivatives like Mint, all pull the same applications from the same servers, Apps that have Unity packages as dependencies will brings those in; apps with XFCE dependencies will bring those in, etc., regardless of which environment they're being installed.  

(I once counted about 30 packages in Mint with "unity" in the name.)

It's a result of the way dependencies work. The libraries, etc., may or may not actually be needed in the "foreign" environment.

It works the other way.  If, say, you want to run the MintMenu on your Ubuntu Mate system, you can add the Mint repos and install it.  You will also install a few Mint dependencies and find a new ".linuxmint" folder in your home directory.

There's nothing of the Unity interface -- the Launcher, the Dash, HUD, the scopes and lenses, web apps, etc. -- in Xubuntu. It's possible, by trial and error, to prune some of the Unity dependencies -- I've done it -- but nothing operational changes. You just have a a fewer files on the drives.

Thanks, BR--I'm really appreciating this.  I've been using Ubuntu pretty much exclusively for eight or nine years--and have been learning all along--but a post like yours really helps to fill in details I've missed.  My impression--hypervigilant, perhaps--is that the Canonical developers aren't particularly friendly to desktop 'power users' and are *very* keen to promote the Unity cross-platform model, possibly to the detriment of the desktop (I find it so)--which clearly is absolutely their right.  When I think about it, my inclination to excise Unity is just an aesthetic one, really--not practically important, as you suggest--except possibly as a minute particle of resistance to trends I find disturbing.

I'm taking Edx's Intro to Linux course and maybe by the time I've finished it, I'll be able to go to straight Debian (over my head for now).  Meanwhile I'm *extremely* glad to have xubuntu/xfce and also grateful for the fine work of the early Ubuntu developers.

Thanks for your time and attention.

---

### Post by mlnease on 2014-08-29
> **vasa1 said:**
> The developers of some apps now include dependencies to cater to the Unity desktop. I've see this with Lubuntu and posted about it here: [http://ubuntuforums.org/showthread.php?t=2181775](http://ubuntuforums.org/showthread.php?t=2181775)

This will probably grow if Unity gets more popular.

Interesting, thanks--and yeah, it does seem likely.

---

### Post by Rob Sayer on 2014-08-30
> **mlnease said:**
> ... I suppose the simple answer is that xubuntu is, at this point, probably inseparable from Unity....

Actually that makes very little sense at all.  They're both based on GTK libraries but you can only take that so far.

I've had more than one DE installed before but I won't do it again unless one is GTK based and one is Qt like KDE.  You can have one DE using a different version of some library components and this can create hard to solve problems.

On this netbook I hopped DEs and distros before 14.04 came out because previously there were hardware support issues.  So whatever fear I had of reinstalling is gone now.  And unless you want to approach this as a learning exercise I think reinstalling xubuntu would be ultimately easier.

if you do reinstall try it with a separate /home partition.  I highly recommend it.

---

### Post by mlnease on 2014-08-30
> **Rob Sayer said:**
> Actually that makes very little sense at all.  They're both based on GTK libraries but you can only take that so far.

I've had more than one DE installed before but I won't do it again unless one is GTK based and one is Qt like KDE.  You can have one DE using a different version of some library components and this can create hard to solve problems.

On this netbook I hopped DEs and distros before 14.04 came out because previously there were hardware support issues.  So whatever fear I had of reinstalling is gone now.  And unless you want to approach this as a learning exercise I think reinstalling xubuntu would be ultimately easier.

if you do reinstall try it with a separate /home partition.  I highly recommend it.

Thanks for this--I really know so little about libraries etc. that this hadn't occurred to me and is useful to know.

As to reinstalling (though I may still fool around a bit, as, as you write, a learning exercise), my first attempt to reinstall from an install DVD (14.04.1) was disastrous--so much so that I reverted to 12.04.  I've installed a couple of dozen mostly Ubuntu distros over the years and this was by far the most troublesome--though subsequently the web upgrade from 12.04 to 14.04.1 went flawlessly.  I may download and burn another ISO DVD and try it again; if I do I'll take your advice and try the separate /home partition option.

Thanks for your time and attention.

---

