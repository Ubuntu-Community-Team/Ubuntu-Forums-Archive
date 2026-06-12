---
title: "Creating a customised Lubuntu 12.04 long term support installation"
date: 2013-03-26
forum: Desktop Environments
---

### Post by OstensiblyFeet on 2013-03-26
I'm wondering if it's possible to create a customised version of Lubuntu 12.04 that would rely on the LTS updates from the main Ubutu Unity version, and receive updates for the LXDE components and other parts with only 18 months support either through a 3rd party repository or by updating those repositories to the ones for 12.10, 13.04, etc. Would this work or would I just end up breaking everything? Can you customise an installation to updates repositories like this?

The idea is to refurbish some old boxes for people who are not particularly technically competent so they can do basic things in an excellent DE without the machines being sluggish, and easily install software using the Software Centre without causing problems.

I do understand why there is no LTS release for Lubuntu given limited resources, but it won't be feasible to hold the hands of the people I'm hoping to benefit from these machines through the upgrade process (backing up, etc.) and if I can ensure they'll receive 4 more years of security upgrades, that will probably be the lifetime of the machines anyway.

I would use XFCE, but the Xubuntu LTS only has two more years anyway, and has noticeably poorer performance on these computers.

Can anyone give me any general advice on this? Am I barking up a completely silly tree?

My other consideration was installing Debian stable with LXDE on top, and then some/most of the repositories for Lubuntu to allow some/most of the same software to run. Does anyone have any experience with that or know whether it's a more or less sensible option?

Cheers in advance!

---

### Post by Frogs Hair on 2013-03-26
Enabling repositories of the newer versions is part of what takes place during an upgrade along with wholesale package replacement . Updaing software packages one at atime would be a lot of work for more than one machine. The sucurity updates are what keep the os viable over the long term and those stop at end of life. I don't think even security updates would be sustainable due to changes in the newer versions.

---

### Post by OstensiblyFeet on 2013-03-27
Thanks for that. That's sort of what I suspected would be the case.

I wonder if my best option is Debian plus LXDE then.

---

### Post by mörgæs on 2013-03-27
Even if it was possible Lubuntu 12.04 is not of LTS-worthy quality.

A large number of bugs are fixed in 12.10 (and even more in 13.04). It you want to experiment it's better to use 13.04 as the foundation.

---

### Post by OstensiblyFeet on 2013-03-27
Those would be based on Ubuntu 12.10 and 13.04 though wouldn't they? So none of the packages would have long term support?

Does anyone know if it's possible to add 3rd party repositories to Ubuntu for LXDE, directly from the LXDE developers for example?

Google points to various pages on this, such as adding a repository, and then installing lxde without the lubuntu-desktop package. What I've found seems to be a bit vague on length of support though, and I'm somewhat unclear about the extent to which LXDE is "supported" in the context of LTS.

I certainly don't mind putting a bit of work in to create a stable system which can then largely be left alone in terms of upgrading the whole distro for a few years.

---

### Post by mörgæs on 2013-03-28
> **OstensiblyFeet said:**
> Those would be based on Ubuntu 12.10 and 13.04 though wouldn't they? So none of the packages would have long term support?


Correct. 
I guess you would be better off by teaching these people how to install. Most people should be able to answer the questions during the installation process.

---

### Post by davesalyers on 2013-03-28
A new "unofficial" LTS version of Lubuntu based on 12.04 already exists and it is called Lubuntu Extra Life Extension. BTW, I'm not the developer just passing on the info.

Here is the link for more info and the download the ISO.

[http://www.lxle.net/index.php?x=about](http://www.lxle.net/index.php?x=about)

LXLE also has a Facebook page at:

[https://www.facebook.com/LubuntuExtraLifeExtension](https://www.facebook.com/LubuntuExtraLifeExtension)

Here is their "Official Release Post":

LXLE Official Release Notes:

After 10 thousand downloads within a month for the beta of LXLE; many suggestions, tips and help came pouring in, it was simply amazing. After some investigating and clever work, its finally official.

Did I miss anything? Probably. Is it flawless? Probably not. Is it a pretty damn nice full featured desktop OS that'll run good/great on any PC made it the past ten years? You bet, but hey, I'm biased.

Needless to say without becoming to long winded, which I'm certainly known to do, lets get to it.

LXLE purpose is to provide a complete, very fast, drop in replacement OS for your aging computer. Its built on an LTS release of Ubuntu, more specifically Lubuntu. Its pretty and ready to go out of the box.

The first official version packs a punch. Most features and graphics from the beta remain intact. However there are significant changes that help complete the OS for an official release.

Best to start with some LXLE unique modifications.

QuickStart App Launcher --- (Alt + z, type to search, enter to launch (arrows navigate))

Aero Snap like feature --- (click on window, hold super key, hit arrow)

Waste Management --- (access trash from panel)

Fast Forecast --- (fast local forecast in panel)

Lubuntu Control Center --- (modified fully working control center)

Deepin Software Center --- (add, remove, find, update, software)

Many replaced and added software titles and repositories to keep you up to date.

Pretty Stuff

Compton --- (menu and window shadows) (only enabled on 64bit)

Greybird --- (complete greybird theme support including openbox, panel)

Elementary --- (updated elementary icon theme)

Wallpapers --- (updated stunning backgrounds)

Conky --- (system gauges on desktop)

Splash Screens --- (elegant startup and shutdown screens)

;)

---

### Post by davesalyers on 2013-03-28
I also found another thread on LXLE which has more information:

[http://ubuntuforums.org/showthread.php?t=2125764](http://ubuntuforums.org/showthread.php?t=2125764)

---

### Post by OstensiblyFeet on 2013-04-03
Cheers for that, I had given LXLE a run already actually. The thing is, as I understand it LXLE relies on some of the Lubuntu 12.10 repositories to keep it supported until April 2014, when the developer plans to create a new version. This means it's based on an LTS Ubuntu release but it doesn't actually have long term support. It's still a really excellent remix of Lubuntu though.

I've installed Debian 6 with LXDE on a machine and it's running very well, although it will take some tweaking to get it nice and user friendly. Debian do have their own version of Software Centre, so I think this is the optimal solution for these users. I need to give it a spin with Debian 7 and see how well it all runs, but as long as there are no serious issues I think that's the solution in this case. Debian 7 will have three years support after it becomes the latest Stable release I think, and that's not long off. So I'll mark this as solved now.

---

### Post by snowpine on 2013-04-03
To clarify: Lubuntu 12.04 gets the same long-term security updates as Ubuntu to its kernel, drivers, applications, etc.
The only piece that is not supported long-term is the LXDE desktkop environment.
What security problems do you predict suddenly arising with the LXDE desktop environment after 18 months in the wild?

---

### Post by OstensiblyFeet on 2013-04-05
I don't. And yes, I've certainly considered that. It seems extremely unlikely that the LXDE packages alone will cause some major security concern, although not being a developer it's not something I'm entirely familiar with. I guess interoperability with other packages could be affected when some go out of date.

Really, it's just a case of better safe than sorry.

---

