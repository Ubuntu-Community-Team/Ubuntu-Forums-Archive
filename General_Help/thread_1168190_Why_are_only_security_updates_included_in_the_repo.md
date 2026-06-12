---
title: "Why are only security updates included in the repositories?"
date: 2009-05-23
forum: General Help
---

### Post by ALIENDUDE5300 on 2009-05-23
I've been using Ubuntu for a while, and I've noticed that even though there's a new version of a software program available, it's not updated in the official repositories, and you often either have to add a custom repository or build it from source. What is the reason behind that? Often newer versions add excellent features, or remove annoyances such as the program CONSTANTLY trying to update (Yes, I'm talking about Vuze). Users may seriously want these features, and unless there is a regression or something that causes issues with other packages, there's no reason not to distribute the updated versions.

---

### Post by mikewhatever on 2009-05-23
Many programs are not made specifically for Ubuntu and require much testing and tweaking and making sure they work fine and don't break anything. Vuse is not really a problem because a newer version can be downloaded from the home page as soon as it's available, and if you don't want it to update, just uncheck the update box, regardless of the version.

---

### Post by ALIENDUDE5300 on 2009-05-23
> **mikewhatever said:**
> Many programs are not made specifically for Ubuntu and require much testing and tweaking and making sure they work fine and don't break anything. Vuse is not really a problem because a newer version can be downloaded from the home page as soon as it's available, and if you don't want it to update, just uncheck the update box, regardless of the version.

The problem with Vuze is that it automatically downloads a new update every time it starts up, fails to installs it, restarts anyways, and repeats the loop. Also, the version in the repositories is ancient. After I downloaded the source version of Vuze, I noticed no problems whatsoever with it, so there should be no problems in updating the repositories. The version in the repositories is version 3.1.1.0, but the latest version is 4.2. That's a huge version difference. They don't even have the same GUI.

---

### Post by mikewhatever on 2009-05-23
Just to clarify, why should there be no problem with updating the repositories? Is it because you noticed no problems?

---

### Post by kerry_s on 2009-05-23
> **ALIENDUDE5300 said:**
> I've been using Ubuntu for a while, and I've noticed that even though there's a new version of a software program available, it's not updated in the official repositories, and you often either have to add a custom repository or build it from source. What is the reason behind that? Often newer versions add excellent features, or remove annoyances such as the program CONSTANTLY trying to update (Yes, I'm talking about Vuze). Users may seriously want these features, and unless there is a regression or something that causes issues with other packages, there's no reason not to distribute the updated versions.

ubuntu is built on debian unstable, unstable is well **unstable** if it were constantly updated the breakages would be more than people could stand.

if you want a good rolling release try debian testing, the stuff has already been through unstable so it's fairly well tested and theres a whole lot less risk of breakage. i haven't had a single break on my other systems.
you just install once and update from there on, no need to keep up with releases.
[http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso)

---

### Post by growled on 2009-05-23
Ubuntu basically takes a snapshot of Debian Unstable and freezes it. They only allow security updates because these usually don't affect stability. If they were to allow program updates that would have allow possible massive instabilities due to conflicting libraries. At least, this is the way I understand it. Rolling releases like Debian Unstable are notorious for breaking things.

---

### Post by colau on 2009-05-23
> **kerry_s said:**
> ubuntu is built on debian unstable, unstable is well **unstable** if it were constantly updated the breakages would be more than people could stand.

if you want a good rolling release try debian testing, the stuff has already been through unstable so it's fairly well tested and theres a whole lot less risk of breakage. i haven't had a single break on my other systems.
you just install once and update from there on, no need to keep up with releases.
[http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso)

[COLOR="DarkSlateGray"]ubuntu is built on debian unstable!!![/COLOR]

---

### Post by snowpine on 2009-05-23
Ubuntu is a stable release linux distribution. Major upgrades to applications are lumped together every six months. By upgrading to a new Ubuntu distribution (Intrepid, Jaunty, Karmic, etc) you get new versions of all the applications. This type of release makes your system more stable, because versions of applications x, y, and z are all tested to work together, and everything gets upgraded at the same time. All you get within the six month cycle is bug fixes and security patches.

Some linux distributions (Arch, Debian Sid, etc) are "rolling release" which means you get new versions of applications as soon as they are available. Ubuntu is not a rolling release distribution; its emphasis is on being stable rather than cutting edge.

Hope that helps clear things up.

---

### Post by lswb on 2009-05-23
> **growled said:**
> Ubuntu basically takes a snapshot of Debian Unstable and freezes it. They only allow security updates because these usually don't affect stability. If they were to allow program updates that would have allow possible massive instabilities due to conflicting libraries. At least, this is the way I understand it. Rolling releases like Debian Unstable are notorious for breaking things.

Yes, with ubuntu, things only break at 6 month intervals.

---

### Post by louieb on 2009-05-23
> **lswb said:**
> Yes, with ubuntu, things only break at 6 month intervals.

rofl - how true.

---

### Post by 3rdalbum on 2009-05-23
Ubuntu is a commercially-supported distribution. System administrators want the ability to get security fixes without actually getting new versions of software - new versions means new bugs. New versions means calls from users asking where xyz feature has moved to. New features may even mean more potential security problems, or may change accepted command-line arguments to the point where scripts will break.

While I can't imagine anyone using Vuze in enterprise, the fact remains: Ubuntu is a stable-release platform, not a rolling-release platform. We get bugfixes and security fixes, but not new versions (unless they are solely fixes).

EDIT: I use Transmission (similar software, really) on a home server that is designed to just run and run without being maintained. I'd hate it if a new version of Transmission was pushed out that causes my nightly "no-uplimit no-downlimit" Cron job to fail due to a change in the command-line arguments, or changed the default port for listening to requests on the web interface, or something like that.

---

### Post by Yellow Pasque on 2009-05-23
You could use a rolling release distro like Arch Linux or Sidux (Xfce/KDE)

---

