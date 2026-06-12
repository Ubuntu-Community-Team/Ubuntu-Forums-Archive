---
title: "How to install Gnome 3.14 in Ubuntu 14.10?"
date: 2014-10-24
forum: Desktop Environments
---

### Post by THPubs on 2014-10-24
How can I install Gnome 3.14 in the new Ubuntu 14.10? I saw some guides saying that we have to add three separate repositories :


```
     sudo apt-add-repository ppa:gnome3-team/gnome3
     sudo apt-add-repository ppa:gnome3-team/gnome3-staging
     sudo apt-add-repository ppa:ricotz/testing

```

Is it necessary to add all three? Isn't gnome3-staging enough?

---

### Post by EmpireITtech on 2014-10-24
```
[COLOR=#555555][FONT=consolas]$ sudo apt-add-repository ppa:gnome3-team/gnome3[/FONT][/COLOR]
[COLOR=#555555][FONT=consolas]$ sudo apt-add-repository ppa:gnome3-team/gnome3-staging[/FONT][/COLOR]
[COLOR=#555555][FONT=consolas]$ sudo apt-add-repository ppa:ricotz/testing[/FONT][/COLOR]
[COLOR=#555555][FONT=consolas]$ sudo apt-get update[/FONT][/COLOR]
[COLOR=#555555][FONT=consolas]$ sudo apt-get dist-upgrade[/FONT][/COLOR]
```

---

### Post by rbmorse on 2014-10-30
base + staging is adequate, but there are bugs and it appears to me many of the bug fixes are being held in testing, at least for now. 

You can start with base + staging and add testing later if you see a need.

---

### Post by ch1mp on 2014-12-06
Hi,

I installed 3.14 without the testing ppa and I was 95% happy, then I updated to 3.14.1 and a few things broke. I added the testing ppa and I've still got a few niggles, so I was wondering does 3.14.2 fix most of the problems in 3.14.1 and how do you install it? 

gnome-shell --version gives me "GNOME Shell 3.14.1" still with the testing ppa enabled. Will 3.14.2 be coming to testing and staging soon?

If not has anyone got a guide on how to compile the sources and install them? Seems like tons of packages to do that one by one would be quite an undertaking...

Thanks,

Tom.

---

### Post by buzzingrobot on 2014-12-06
Building Gnome:  [https://developer.gnome.org/jhbuild/stable/getting-started.html.en](https://developer.gnome.org/jhbuild/stable/getting-started.html.en).

Not a task for the casual user, though. You'd very likely find the same bugs and issues that the Ubuntu Gnome team has found.

---

### Post by ch1mp on 2014-12-06
Thanks for that, what are the bugs and issues the Ubuntu Gnome team have found? 

Will it take a while for a stable 3.14.2 on Ubuntu?

---

### Post by buzzingrobot on 2014-12-06
> **ch1mp said:**
> Thanks for that, what are the bugs and issues the Ubuntu Gnome team have found? 

Will it take a while for a stable 3.14.2 on Ubuntu?

Ubuntu Gnome bugs: [https://bugs.launchpad.net/ubuntu-gnome](https://bugs.launchpad.net/ubuntu-gnome).

Gnome bugs:  [https://bugzilla.gnome.org/browse.cgi](https://bugzilla.gnome.org/browse.cgi).

Remember, anyone who bothers to create an account at those sites can report a bug.  What they report may or may not actually be a bug, or a bug that anyone else can duplicate, or a bug that impacts anyone else, or can actually be fixed, or a bug a developer decides to fix.

The issue with Ubuntu Gnome staying current with Gnome releases is that both follow a fixed release cycle and those cycles are out of sync.  Offical Ubuntu releases, like Ubuntu Gnome, follow a six-month release cycle.  So does Gnome.  But, Gnome's release schedule sees it release a new Gnome version about one month before a new Ubuntu release is due. By then work on the next Ubuntu Gnome release, which began 5 months earlier, is far down the road. One month hasn't been enough time to incorporate that new Gnome release into the next Ubuntu Gnome release and still meet the requirements and deadlines entailed in being an official Ubuntu flavor.

I'm sure the Ubuntu Gnome team would like each release to fully incorporate the latest Gnome version, and maybe they'll find a way with 15.04.

---

### Post by ch1mp on 2014-12-09
Yeah I'm aware fo them being out of step, that's why I was keen to move from the 3.12 in the release to the newer 3.14. 

 Since then there's been the update to 3.14.1 which broke a few things (for me at least, I've since manually fixed the most annoying stuff, like Files not opening from the launcher etc.) and the release of 3.14.2. As yet though using the PPAs mentioned above there are no signs of 3.14.2 landing yet.

I was really just wondering when there might be an update to the PPAs, and if there wasn't to be any how easy it would be to build it myself. You've answered that with teh link to the developer section on the GNOME site though and it's not trivial by any means.

---

