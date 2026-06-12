---
title: "Ubuntu Linux 18.04 with DE KDE Plasma 5.13?"
date: 2018-05-25
forum: Desktop Environments
---

### Post by la.khan on 2018-05-25
Hi,


Earlier this month, I installed Ubuntu Linux 18.04 (64 bit) with default DE Gnome 3.28.1. I have heard good things about DE KDE Plasma 5.13 and wish to try it out.


Can I install KDE Plasma 5.13 over Ubuntu Linux 18.04 (64 bit)?


What are the implications of this setup (Ubuntu Linux 18.04 (64 bit) & KDE Plasma 5.13), applications wise - Firefox 60.0.1, Chromium 66, LibreOffice 6.0, Master PDF editor 5 etc?


I installed some Gnome 3.28.1 extensions. Will these work with KDE Plasma 5.13? Or, these extensions are meant to work with Gnome DE and are irrelevant in KDE Plasma scheme of things?


Anything I need to watch out for?


Thanks for your replies!

---

### Post by Paul Barnett on 2018-05-25
had the same problem. I had ubuntu 18.04 installed and tried to install Kubuntu beside it. Kubuntu works great but Ubuntu will not open.

---

### Post by axiomanarcho on 2018-05-25
I use a active version of kde neon but you can add the neon repositories to your install. [https://forum.kde.org/viewtopic.php?f=309&t=135278](https://forum.kde.org/viewtopic.php?f=309&t=135278)

---

### Post by axiomanarcho on 2018-05-25
You will get the beta version of kde5.13 which will be 5.12.80

---

### Post by axiomanarcho on 2018-05-25
Gnome extensions wont work with plasma there are a huge collection of plasma widgets and extensions on kde store.

---

### Post by monkeybrain20122 on 2018-05-25
Why don't you just install kubuntu? Mixing several DE is never a good idea IMO and you get a lot of extra junks and potential conflicts creeping up in unexpected places (granted some people would disagree and say they have 100 different DEs on the machine) If you dualboot then  I suggest dualbooting with a different distro at least you get something different besides the DE (e.g I heard Opensuse has the nicest KDE implementation though I have never used it myself) It is kind of pointless to have two different flavours of Ubuntu on same machine.

---

### Post by QIII on 2018-05-25
@Paul Barnett -- yours is not the same problem, as the OP described no problem.  Please start your own thread if you are seeking support.

@axionmarco -- there is no need to add the repos from a different distro.  That would, in fact, be a decidedly bad idea as KDE Neon may have any number of dependencies that are different from Ubuntu and that might render the OP's machine inoperable.  Please refrain from providing such dangerous advice.  KDE is available in Canonical's repos.

---

### Post by axiomanarcho on 2018-05-25
Yeah doing further reading it is wise to install kubuntu... as a default install, I wouldn't suggested the kde neon repository unless you install neon seperately.

---

### Post by la.khan on 2018-05-26
> **axiomanarcho said:**
> You will get the beta version of kde5.13 which will be 5.12.80
Thanks for pointing that out. I realize now that KDE Plasma 5.13 is still in beta/development; this will be released on 12th June. So, I may wait another 2-3 weeks before I decide to install DE KDE Plasma 5.13.
> **monkeybrain20122 said:**
> Why don't you just install kubuntu? Mixing several DE is never a good idea IMO and you get a lot of extra junks and potential conflicts creeping up in unexpected places (granted some people would disagree and say they have 100 different DEs on the machine) If you dualboot then I suggest dualbooting with a different distro at least you get something different besides the DE (e.g I heard Opensuse has the nicest KDE implementation though I have never used it myself) It is kind of pointless to have two different flavours of Ubuntu on same machine.
I am familiar with Ubuntu Linux 14.04/16.04 (64 bit) with Unity desktop. I never realized in the last few years there were other DEs available. Last year, when Canonical announced 18.04's  default desktop will be Gnome, I installed Gnome for Ubuntu Linux 16.04. Now, I have performed a fresh install of Ubuntu Linux 18.04 (64 bit) with Gnome 3.28.1.
After installing the latest UL 18.04, I hear of DE KDE Plasma 5.12/13. I like UL 18.04 with Gnome, Gnome extensions etc but I wish to see if KDE Plasma 5.12/13 is better. Only way to find out is to install and use it, see for myself if I feel KDE Plasma 5.12/13 works for me better than Gnome 3.28. If I think KDE Plasma offers me more customization options, applications, widgets, for my next update/upgrade, I may opt for Kubuntu.

Right now, I am certain I don't want any dual boot on my laptop, even if they are two versions of Linux. I just wish to test drive KDE Plasma 5.12/13. I feel the best way to do it is installing KDE Plasma 5.13.

When KDE Plasma 5.13 is released next month, I will install it. I have the instructions in this URL: [https://linuxconfig.org/how-to-install-kde-plasma-desktop-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-install-kde-plasma-desktop-on-ubuntu-18-04-bionic-beaver-linux)
I hope this installs DE KDE Plasma 5.13 and not the entire Kubuntu 18.04 OS.

---

### Post by SeijiSensei on 2018-05-26
One good way to "test drive" a distribution is by using a virtual machine.  You can install VirtualBox on your current Ubuntu machine, then install Kubuntu 18.04 into the VM.  Follow the procedure here to install VirtualBox:  [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

You can install Kubuntu into the VM directly from the ISO file.

---

### Post by monkeybrain20122 on 2018-05-26
> **SeijiSensei said:**
> 
You can install Kubuntu into the VM directly from the ISO file.


I think most of the KDE's effects won't work in VM because graphic driver in VM only has rudimentary OpenGL support .OP seems to be interested in the bells and whistles KDE has to offer so VM will be a disappointment.

---

### Post by SeijiSensei on 2018-05-27
> **monkeybrain20122 said:**
> I think most of the KDE's effects won't work in VM because graphic driver in VM only has rudimentary OpenGL support .OP seems to be interested in the bells and whistles KDE has to offer so VM will be a disappointment.

Even with the proprietary driver in the Extension Pack?

I don't care much about those "bells and whistles" so my advice may be off-base.  In that case the OP should boot a distro into "Try Ubuntu" mode to use the actual hardware.

---

### Post by monkeybrain20122 on 2018-05-27
> **SeijiSensei said:**
> Even with the proprietary driver in the Extension Pack?

I don't care much about those "bells and whistles" so my advice may be off-base.  In that case the OP should boot a distro into "Try Ubuntu" mode to use the actual hardware.


  OP didn't say he has a Nvidia card (or I might have missed it) but even if he does, I still don't think it will work. VM uses its own graphic driver, what works for the host doesn't descend as far as I know.

---

### Post by la.khan on 2018-05-27
> **monkeybrain20122 said:**
> OP didn't say he has a Nvidia card (or I might have missed it) but even if he does, I still don't think it will work. VM uses its own graphic driver, what works for the host doesn't descend as far as I know.
No, I don't have any special graphics card installed. My laptop has graphics card integrated with the motherboard.
In the past, I could change/add HDD & RAM in my desktops and laptop. I thought I can buy a graphics card and put it into my laptop anytime. It was only recently I learnt that I cannot add a graphics card to my laptop :( as graphics card is different from adding/changing RAM. For my next laptop, I plan to get 1/2/4 GB graphics card.

---

### Post by la.khan on 2018-06-14
Hi all,

Just want to update the thread.

Yesterday, I installed KDE Plasma 5.13 successfully. Let me play around with the DE (widgets and other bells & whistles) to see if it is better than Gnome 3.28. Thanks to all for your advice!

Let me mark this thread as closed ):P

---

