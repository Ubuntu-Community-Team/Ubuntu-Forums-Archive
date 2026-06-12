---
title: "Why is software updating in Ubuntu so troublesome?"
date: 2009-02-19
forum: General Help
---

### Post by Eice on 2009-02-19
Hi,

One of the advantages about Linux I'd heard of long ago was the ease of software installation and upgrades. Everything was supposed to be in the repositories, and unlike Windows where you had to update pieces of 3rd-party software individually, all you had to do in Linux was to visit these centralized repositories and all the work would be done for you.

I tried Ubuntu for myself a few weeks ago, and this was indeed true; or so I thought. Then I realized my copy of OpenOffice was still version 2.4 when 3.0 had been released since last year. I found the 3rd-party repo for that, and all was well, until I began discovering pieces of outdated software all over my computer even though the Update Manager reports no new updates. Apparently software updates are not pushed to the repos as quickly as they should be. Transmission and Pidgin were out of date, Virtualbox probably is, since I grabbed the .deb package from the website instead of installing via the repos, and god knows what else. To make matters worse, unlike their Windows counterparts, these programs wouldn't automatically check for updates for themselves since Update Manager supposedly does that work for them.

So I tried manual updating by hand, like the old Windows days. Downloaded Pidgin, which turned out to be a tar.gz file with no further instructions on how to compile it. And even if it worked, I'd have no idea when it'd be out of date again.

Am I missing something here, or is the story of Ubuntu being better than Windows at keeping your system up-to-date only a theoretical one?

---

### Post by user-max on 2009-02-19
well, many programs check for newer versions. Like Virtual Box, for example, will let you know about a new release. All the stuff you install via a package manager gets updated through repos, however repos don't get newest versions instantly, since whoever makes the software does not necessarily package it for different distros, and therefore there is a lag. However outdated pidgin can'd do any harm :)

---

### Post by mb_webguy on 2009-02-19
Many distributions of Linux use rolling updates.  That is, as a new version of an application or package is available, it is added to the repository, and thus the distribution is progressively updated.

Ubuntu, on the other hand, has a stepped update policy.  A new version of Ubuntu is released every six months.  Slightly before the time of each release, the repositories for that version are frozen, and no new versions of packages may be added except for security updates and bug fixes.  There are both advantages and disadvantages to this.  

The most obvious disadvantage is one you've already noted -- that applications in the repositories are often not the most recent available.  However, a big advantage is that all of the packages can be tested against a known package structure, rather than one that's constantly changing.  Average desktop users generally don't need the latest, greatest version of every application.  What they *do* need is a system that works and works consistently, without an update significantly breaking things.  For these users, a stepped system is the better way to go. 

For those users who *do* want the latest and greatest applications, and want them available through the package managers like Update Manager and Synaptic, Canonical (the company behind Ubuntu) created Launchpad, where users and developers can create their own personal repositories.  PPAs (Personal Package Archives) can be added to your software sources and used exactly like the official repositories.  In some cases they're maintained by individuals, like yourself, who have a need for the latest releases of certain applications.  In other cases they're maintained by software development projects (like [openoffice-pkgs]("https://launchpad.net/~openoffice-pkgs/+archive/ppa") and [deluge-team]("https://launchpad.net/~deluge-team/+archive/ppa")), as a way of distributing their software.

But basically, if you want a distribution whose official repositories always contain the recent versions of applications without any extra work on your part, Ubuntu's not the best choice for you.  On the other hand, if you want a distribution that has packages well-tested against a known set of packages to ensure minimum conflicts, and for which you have the option of adding specialized repositories for more recent versions of software than what may be in the official repositories, then Ubuntu's the one you want.

---

### Post by Eice on 2009-02-19
Thanks for the answers, user-max and webguy. Problem not solved, but at least now I know why this is happening.

I'll see if I can figure out more about Launchpad. Thanks again.

---

### Post by benmoran on 2009-02-19
mb_webguy hit the nail on the head. I use the default repositories for 99% of things, but for a few select programs I use PPAs. It's easy to add these to your sources (repository) list either using the command line or via System/Administration/Software Sources. 

I love having the newest version of programs such as Transmission and Wine. The PPA (Launchpad) system allows this easily. Having the programs check for updates themselves seems convenient, but it really really becomes an irritation after you get used to the repository system.

---

### Post by Mercury_Alpha on 2009-02-19
Yeah, the only major exception I know of is Wine, which uses the PPA only for its bleeding-edge builds, and another domain (budgetdedicated.com) for its stable builds that haven't hit the official Ubuntu repos yet.

---

### Post by Archmage on 2009-02-19
If you think that Ubuntu is hard, try installing the latest KDE in Windows. :D

---

### Post by kaivalagi on 2009-02-21
> **Archmage said:**
> If you think that Ubuntu is hard, try installing the latest KDE in Windows. :D

+1 :)

Or have a crack at Gentoo :lolflag:

---

