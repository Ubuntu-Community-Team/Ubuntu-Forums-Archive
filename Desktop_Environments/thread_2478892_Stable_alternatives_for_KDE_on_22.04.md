---
title: "Stable alternatives for KDE on 22.04?"
date: 2022-09-07
forum: Desktop Environments
---

### Post by Peter_Brandon on 2022-09-07
I recently upgraded to Ubuntu 22.04, but I am finding it seriously buggy with respect to the desktop I use--KDE.  Last week there was a kernel update that wreaked havoc on the stability of applications in my Virtualbox guest OS's.  I found a fix to that, but it took a day and a half.  This week, after updating a couple peripheral-seeming packages and rebooting, KDE is suddenly without panels or background and I can't restart them from the terminal.

I need to get non-IT work done, not spend time finding workarounds for bugs.  I also don't have to have the latest, hottest, buggiest software.  So what do folks out there recommend for a highly stable distro with KDE?  Maybe I should have installed Kubuntu directly rather than adding KDE desktop to Ubuntu?  Have also heard about MX, Fedora, maybe OpenSUSE, Neon.

---

### Post by QIII on 2022-09-07
Hello!

If you added a DE to another flavor, then updates can be a mixed bag -- sometimes full of things you don't like.

Still, I had problems with a release upgrade to Kubuntu 22.04 and ended up having to just reinstall afresh.  Pretty easy to do since I had a good backup and a separate home partition.

That went fine and I've had no problems.  

Something wasn't right in the upgrade packages from Canonical.  That doesn't mean that KDE is unstable.  It has always been rock solid for me except for this one case, which really was not the fault of KDE.

---

### Post by SeijiSensei on 2022-09-08
> **Peter_Brandon said:**
> I need to get non-IT work done, not spend time finding workarounds for bugs.  I also don't have to have the latest, hottest, buggiest software.  So what do folks out there recommend for a highly stable distro with KDE?
Maybe you should try Kubuntu 20.04 instead: [https://cdimage.ubuntu.com/kubuntu/releases/20.04/release/](https://cdimage.ubuntu.com/kubuntu/releases/20.04/release/)

---

### Post by guiverc on 2022-09-08
I'll give my thoughts, by it's only opinion & I don't have any real answers.

I'm a lover of multiple DEsktops on my systems, but there can be problems with them, esp. if you add/remove them then later add/remove others.. The most stable systems I've found for multiple DEs are firstly Debian, secondly would be openSuSE.  Fedora is about equal to Ubuntu in that regards (*in my experience*); two or three can be installed (or installed/removed) before issues can occur, but as you hit four problems/conflicts can occur, or at five problems should be expected.  

Your didn't provide enough details for any opinion as to what your issue is, but do mention kernel update? - which won't impact the desktops themselves (*kernel updates impact kernel modules - aka video drivers rather than the DE*). I have experience with some older video cards that have issues with KDE & GNOME with upgraded kernels/modules your description seems closer to - but those don't relate at all to the KDE being used (ie. boot the latest Qt5/KF5/KDE or an older Qt5/KF5/KDE on older kernel, or newer kernel & the issue relates to kernel/kernel-modules not the KDE stack) - ie. your blaming KDE on a kernel modules seems to be mixing two rather different things to me.

I think stability between Ubuntu (*including flavors like Kubuntu*), Debian, openSuSE & Fedora are about ~equal.. the difference I see as mostly *timing *related to when the packages are grabbed from upstream.

KDE Neon exists for those wanting the latest KDE & are willing to *risk* a bit of *stability.  *If you need later KDE in Kubuntu, two backport options exist; the safer option will be in between Kubuntu & KDE Neon, the *riskier* Kubuntu backports (with newest KDE) choice closest to KDE Neon. I thought however you wanted to increase *stability* though?

You can re-install Ubuntu (*and flavors*) rather easily..

Fedora will require more recent upgrades; a release goes EOL one month after two subsequent releases.. ie. you're looking at 12-13 months of *supported* life if you're not using *rawhide*; and *rawhide* isn't intended to be *stable*.

OpenSuSE *tumbleweed* is a little more maintenance *heavy* in my experience (*the box to my left is currently performing its dist-upgrade... 3726 packages being upgraded and it takes awhile*) when compared with Debian *testing/bookworm* or the box I'm replying here on (Ubuntu *kinetic*). If contrasting OpenSuSE *leap*, it has a longer *supported* life than Fedora; but it's still shorter than Ubuntu LTS.  Supported life impacting maintenance of the box of course.

In my experience, the non-LTS upgrade path is less problematic, than the LTS-LTS path, but that's mostly as I only have six months of changes that I've made to deal with, rather than two years of somewhat forgotten complications.. Given Ubuntu releases are very well known; 22.04 = 2022-April, next LTS will be 2024-April and most likely the 3rd of 4th Thursday of the month! thus are easiest to plan for which helps with planning...

To me the biggest difference relates to *support*, as stability I find pretty much equal.... (*writing as a user of Debian, Ubuntu (including flavors; Lubuntu now but I still consider that Ubuntu*), Fedora, & OpenSuSE.

---

### Post by Peter_Brandon on 2022-09-08
Thanks QIII:  I should have been more clear.  When I said 'upgraded to Ubuntu 22.04' what I actually meant was that I wiped my system clean and installed 22.04 from a live USB.  I've been running into many problems, but the two I mentioned rendered either all of KDE unsuable or a big part of what I use (Virtualbox OS's), unusable.  Other problems include not being able to directly access the repository gui or ksystemlog--it won't take my password (known bug); flickering on parts of the screen after resume from suspend; flickering takes over screen forcing a reboot; save session not working properly; and so forth.  At least on my computer, KDE running on Ubuntu 22.04 hasn't seemed stable even after a clean install.

---

### Post by Peter_Brandon on 2022-09-08
Thank you SeijiSensei!  I'm wondering how Kubuntu 20.04 would differ from Ubuntu 22.04 running KDE, which also flashes the Kubuntu logo on startup?  Is there reason to think Kubuntu would be more stable?

---

### Post by SeijiSensei on 2022-09-08
You could install Kubuntu 22.04 if you want the latest and greatest, but 20.04 still has support through 2025. Since you said you valued stability over cutting-edge software, 20.04 might be the best choice.

Unlike guiverc I never install KDE or any other desktop environment on top of a vanilla Ubuntu installation. I always use Kubuntu which is designed for KDE. Similarly if I wanted an LXDE desktop I'd install Lubuntu. With virtual machines I find having multiple VMs with different distributions better than one system with multiple desktops.

I tried Neon for a while, but came back to Kubuntu. If you want to stay up-to-date with the latest version of Plasma, you can add the Kubuntu "backports" PPA: [https://launchpad.net/~kubuntu-ppa/+archive/ubuntu/backports](https://launchpad.net/~kubuntu-ppa/+archive/ubuntu/backports)

I've abandoned VirtualBox in favor of the VM system built into the Linux kernel: [https://www.tecmint.com/install-kvm-on-ubuntu/](https://www.tecmint.com/install-kvm-on-ubuntu/)

---

### Post by Peter_Brandon on 2022-09-08
guiverc:  Thanks for much food for thought!  You make excellent points about the suitability of Neon (which people keep recommending to me), Fedora, and OpenSuSE.

I should mention that I don't run many desktop environments.  I installed minimal Ubuntu, then KDE desktop, and have run KDE ever since.  So I've had Gnome and KDE, but haven't used Gnome till now--I fell back to it when KDE went belly up.

I'm still under the impression that KDE under Ubuntu 22.04 has just too many problems--besides the problems I mentioned that make it impossible or difficult to get work done, there have also been a multitude of other issues.  You are right that I shouldn't blame KDE for the VirtualBox instability that ensued after a kernel update (and that many others have reported in LaunchPad).  But that doesn't change the fact that KDE + Ubuntu 22.04 ran into a substantial problem in this case that might not have appeared on another base OS such as Debian Stable.  (I doubt Stable is using the bleeding edge kernel Ubu is).  

Given the points you make, I'd guess my best option is Debian Stable, provided I can handle the driver installation issues there (Broadcom, Nvidia, CUDA, etc.).  I like the idea of running multiple OS's.  My current system, however, is lvm with only root and boot partitions and it's encrypted.  I'm guessing I could make a copy of my home directory (which has software like Anaconda--but hopefully that will run on a copy), erase it, add some partitions, put the copy of home on its own partition, and use a spare partition or two to experiment with Debian Stable and whatever else.

My other option might be to see if I can work in Gnome, which is already installed on my system.  It just doesn't seem to have the power user capabilities KDE has, at least as initially installed.  The Cairo dock has helped a lot and apparently I can still use dolphin, though wonder whether it will run into incompatibility issues.  Can't get session saving to work.

---

### Post by Peter_Brandon on 2022-09-09
Thanks SeijiSensei!  Ubuntu releases every two years, so I thought they  would stop support about every 2 years, but now that I look it's 5 years  of general support and 10 years of security support, which is  terrific.  I had Ubuntu 20.04 with KDE desktop but upgraded seeing it  was some months since 22.04 came out and thinking that support for 20.04  would soon end.  Should consider a down-grade.  You are right that  multiple desktops seem to trip each other up, if not worse.  Now that  I'm using Gnome (KDE is busted), I get crashes of KDE software that's  running in the background.  Also thanks for mentioning the kvm  option--something I should consider, esp when VBox runs into problems!

---

### Post by guiverc on 2022-09-09
> **Peter_Brandon said:**
> Ubuntu releases every two years, so I thought they  would stop support about every 2 years, but now that I look it's 5 years  of general support and 10 years of security support, which is  terrific.

I'll try and clarify a little here..

A recent [Ubuntu 22.04.1 LTS Released announcement]("https://fridge.ubuntu.com/2022/08/12/ubuntu-22-04-1-lts-released/") contains the following

> Maintenance updates will be provided for 5 years for Ubuntu Desktop,  Ubuntu Server, Ubuntu Cloud, and Ubuntu Core. All the remaining flavours  will be supported for 3 years. Additional security support is available  with ESM (Extended Security Maintenance).

Flavors of Ubuntu (eg. *Kubuntu you mention; or the Lubuntu I'm heavily involved with*) are *community* supported, thus have three years of support for a LTS release.

ps:  If you want to explore on your own system, use `ubuntu-security-status` (or `ubuntu-support-status` for older releases)

Packages included on the main Ubuntu Desktop, Ubuntu Server, Ubuntu Cloud, or Ubuntu Core installation media come with 5 years, those packages came from the 'main' or a repository that has 5 years of support (*with no packages from 'universe' included* *on media unlike the flavor ISOs*).

if you reach the end of *standard support* (*for 22.04 LTS that will mean 2027-April; 5 years from initial release in 2022-April [22.04]*) and wish to *enable* ESM support; you will get a further 5 years of *extended security maintenance *support for the packages that receive support with ESM; which is usually a [*large*] subset of those included on initial media (as an example; looking at prior releases that switched to ESM [eg. 16.04 [here]("https://wiki.ubuntu.com/SecurityTeam/ESM/16.04")] at EOSS may provide a clue; which can require switching from default *deb* packages to *snap* for some). ESM is really intended for corporations that have mission critical processes they cannot afford  to change; not the average desktop user - so I'd consider Ubuntu as having 5 years as per the release announcements (*deciding to use ESM if you really need to*)

For more [detail on repositories, this link]("https://help.ubuntu.com/community/Repositories/Ubuntu") maybe helpful.

---

### Post by darkshvein2 on 2022-09-10
> **Peter_Brandon said:**
>  This week, after updating a couple peripheral-seeming packages and rebooting, KDE is suddenly without panels or background and I can't restart them from the terminal.
I try suggest; Did you try to replace kwin wayland to xorg version? wayland so buggy for working(with my open radeon card drvs) 

also, after upgrade to 22.04 I had problems too:
[https://ubuntuforums.org/showthread.php?t=2478645](https://ubuntuforums.org/showthread.php?t=2478645)

is not kde problem, all packages already fixed in mainstream.
this is maintainer issue.

---

### Post by Peter_Brandon on 2022-09-11
Thank you guiverc!  That's quite helpful information.  Five years is still quite good.

---

