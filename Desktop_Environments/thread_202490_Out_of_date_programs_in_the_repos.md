---
title: "Out of date programs in the repos"
date: 2006-06-23
forum: Desktop Environments
---

### Post by bailout on 2006-06-23
I have come across a couple of programs from the reps recently that are quite out of date. Kmymoney is version 8.2 which was released in Dec 2005 but they released 8.3 in Feb and 8.4 in May. I know the May release was probably a bit late to make Dapper but I would have thought the Feb release should have made it. There is a deb available but it has lots of missing dependencies because it obviously isn't packaged for Dapper.

The other program is Apollon which looks like the rep version is from 2004 but the update in 2005 hasn't been included. Again I think it is in the Debian reps.

I don't really know how the Ubuntu reps sync with Debian and whether the problem is Debian being slow moving the new packages from unstable to stable or whether the problem is with Ubuntu.

I would rather just use ubuntu rep packages as much as possible but I am wondering whether the best thing is to learn to compile/package myself. If I make packages myself will it cause problems when updating in the future?

---

### Post by ifokkema on 2006-06-23
[QUOTE=bailout]I don't really know how the Ubuntu reps sync with Debian and whether the problem is Debian being slow moving the new packages from unstable to stable or whether the problem is with Ubuntu.[/QUOTE]
It takes ages for a package to go to stable, since the stable releases are the official ones, actually getting an own code name and all. I believe there was some three years between the current stable release, Sarge, and it's predecessor, Woody.

The Ubuntu releases are not as stable as the Debian stable releases, but therefor, contain lots of newer software. Then again, as you have notices, they aren't like Debian unstable either.

[QUOTE=bailout]I would rather just use ubuntu rep packages as much as possible but I am wondering whether the best thing is to learn to compile/package myself. If I make packages myself will it cause problems when updating in the future?[/QUOTE]
No. You can compile an program and build a neat .deb package using checkinstall. Then you can easily uninstall the program using dpkg, if you want to. Also, if a version is available through the reposotories which is actually newer than the version you have, it will be replaced nicely (provided you configure the installed package, including it's version, correctly).

---

### Post by bailout on 2006-06-24
Is there any way I can request updated versions from the ubuntu developers? I have had a browse on making debs and it sounds pretty complicated and beyond me I think. If I can get ubuntu to update the packages for edgy then they will become eligible for backports to dapperise them.

---

### Post by arsenic23 on 2006-06-24
[QUOTE=bailout]I have had a browse on making debs and it sounds pretty complicated and beyond me I think.[/QUOTE]

Did you see this tutorial: [http://www.ubuntuforums.org/showthread.php?t=51003&highlight=making+.deb](http://www.ubuntuforums.org/showthread.php?t=51003&highlight=making+.deb)

I found it made building .debs pretty simple, and I had to use it to get a version of conky that would work correctly.

---

