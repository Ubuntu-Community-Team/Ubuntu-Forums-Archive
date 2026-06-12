---
title: "KDE from source"
date: 2006-01-20
forum: Desktop Environments
---

### Post by BrianB on 2006-01-20
How, roughly would I go about compiling KDE 3.5 from source and is there anyway to build binary .debs from the source for easy install/uninstall?

---

### Post by cwaldbieser on 2006-01-20
[QUOTE=BrianB]How, roughly would I go about compiling KDE 3.5 from source and is there anyway to build binary .debs from the source for easy install/uninstall?[/QUOTE]
KDE has a tool called "konstruct" that makes building the core easier.  
[http://developer.kde.org/build/konstruct/]("http://developer.kde.org/build/konstruct/")
I don't know if there is an easy way to deb-ify it, though.

---

### Post by raggamuffin on 2006-01-20
[QUOTE=BrianB]How, roughly would I go about compiling KDE 3.5 from source and is there anyway to build binary .debs from the source for easy install/uninstall?[/QUOTE]

what version of KDE are you using right now?...if you just wanna upgrade to 3.5 from an earlier version, all you have to do is follow the instructions at [http://kubuntu.org/announcements/kde-35.php](http://kubuntu.org/announcements/kde-35.php) and "sudo apt-get update &&sudo apt-get upgrade"

this will be much easier than compiling from source (unless you have a specific reason for wanting to compile from source)...

---

### Post by BrianB on 2006-01-20
Thanks for the reply, I'm currently using GNOME so it really would be easier to have debs and as i'm on dial-up it would take forever to download from Synaptic . Does anybody know if it can be done?

---

### Post by der_joachim on 2006-01-21
[QUOTE=BrianB]How, roughly would I go about compiling KDE 3.5 from source and is there anyway to build binary .debs from the source for easy install/uninstall?[/QUOTE]

When I still used Debian, I used to compile a lot of stuff, the gentoo way. There used to be a website dedicated to that one, but I did not manage to find it in my bookmarks. It was something like debtoo.org, but not quite. :)

Sometimes there was a slight performance boost, but don't expect any miracles.

At least you need the package apt-build.

---

