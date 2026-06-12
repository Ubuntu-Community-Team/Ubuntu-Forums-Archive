---
title: "Questions about Edgy Eft, checking for bugs, upgrades"
date: 2006-08-16
forum: Desktop Environments
---

### Post by theosib on 2006-08-16
I'm not sure if this is the right forum for this post, but I feel it's somewhat more general than just about Edgy Eft, so I thought I'd post it here.  Perhaps a moderator can redirect it to a more appropriate place.

Typically, one would think it lunacy to install an unstable release of an OS for one's main desktop.  I had, however, had a good experience with unstable Dapper, and I'd really like to contribute to the debugging process of Edgy Eft in some way.  I have a few questions about that.

Does the update system do a good job of propagating bug fixes to one's unstable install?  That is, if I report something on the bug tracker, it gets fixed, and checked in, and incorporated into a daily build, will the update system install the updated package automatically?  Or do I have to install a new daily build?  When I was using unstable Dapper, I got updates now and then, but I can't be sure if that covered everything.

When Edgy rolls over to become a stable release, will my system automatically update to the latest version of everything and magically become a stable release?  I had an install of Dapper that I'd installed while it was unstable.  I hadn't used it in a long time, and in the mean time, Dapper went stable.  When I booted it up recently, it told me there were no updates available.  Considering the number of bugs I reported, I find that to be MOST strange.

If my Edgy install does get updated to stable by the update system, and then I decide later to upgrade to whatever is the next stable release, will that upgrade work as well as if I'd gone from stable to stable?

The reason I ask all of this is because I want to transition from Gentoo (which has often suffered significant breakage whenever I would upgrade packages) to Ubuntu.  I'd also like to help with Ubuntu.  But what I DO NOT want to do is install an unstable release and then have to wipe it all out completely when Edgy goes stable.  I'm willing to put up with some program crashes and even a limited amount of data loss here and there (I have a habit of saving very frequently when editing documents), but I do not want to have to back up my personal files, wipe everything out, reinstall, and then set all of my bookmarks and preferences again once things go stable.

Suggestions?

Thanks!

---

### Post by zxee on 2006-08-16
From the apt-get man pages:
> dist-upgrade
              dist-upgrade  in addition to performing the function of upgrade, also intelligently handles changing dependencies with  new  ver&#8208;
sions  of  packages;  apt-get  has a "smart" conflict resolution system, and it will attempt to upgrade the most important  pack&#8208;
ages  at  the  expense  of less important ones if necessary. The
/etc/apt/sources.list file contains a  list  of  locations  from
which  to  retrieve  desired package files. See also apt_prefer&#8208;
ences(5) for a mechanism for overriding the general settings for
individual packages.


I don't know how soon bug fixes get into the repos.

I was running a test version of dapper since obtaining the 6.06.1 iso (I'm on a dial up) and using apt to install the upgrade my system has become dapper stable-in all ways. 
So yes you can continually upgrade to the next stable release-that's always been one of the touted claims of debian-debian-based systems. 
Will something eventually break though-hard to tell for sure. 
Theorically there should be no breakage because apt shouldn't allow package upgrade combinations that would cause trouble.

---

### Post by theosib on 2006-08-17
There is no dist-upgrade command on my system.  I'm running Kubuntu.  Would that make a difference?  I have found adept-updater.  Will that do all the same stuff?

---

### Post by murataht on 2006-08-17
> **theosib said:**
> There is no dist-upgrade command on my system.  I'm running Kubuntu.  Would that make a difference?  I have found adept-updater.  Will that do all the same stuff?

do you mean you don't have "apt-get dist-upgrade" ???
:confused: 
it should come with apt-get. check it again.

---

### Post by theosib on 2006-08-17
Actually, I tried "sudo apt-get dist-upgrade", and I got some sort of error.  I'm using other means to update things, so I'll try again when that's done.

---

### Post by theosib on 2006-08-17
Are you sure you spelled "dist-upgrade" correctly?

sudo apt-get install dist_upgrade
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package dist_upgrade

sudo apt-get install dist-upgrade
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package dist-upgrade

---

### Post by zxee on 2006-08-17
To update the bug fix question-somewhat anyway. The 6.06.1 release is approx.
a week old. My system has been up-to-date. Today the update manager told me there were 3 updates to install-they were bugfixes/security. 
I downloaded them and now my system is up-to-date again. Is this heaven-or what!
You can't run apt-get at the same time that you're running synaptic or (sorry you're on kde) adept-updater. You have to have dist-upgrade But I see your problem you don't run apt-get _install_ dist-upgrade because then apt thinks you're looking for a package by that name. the command is:
> sudo apt-get dist-upgrade

---

### Post by Ramses de Norre on 2006-08-17
I'd use aptitude instead of apt-get, the syntax is the same but the dependency solving capacities are way higher =)

---

### Post by theosib on 2006-08-18
If aptitude is so much better, why isn't that the official program to use instead of apt-get?

That's one of the things that drove me nuts about Gentoo.  Using the programs they tell you to use on the wiki yielded poor results in many cases, which I would complain about.  5 people would respond, telling me to use 5 different tools, each of which is "the best".  A person can't keep track.

---

### Post by danyer on 2006-09-03
Theosib,

type: apt-get dist-upgrade

and not: apt-get install dist-upgrade

Good luck,
Dan.

---

