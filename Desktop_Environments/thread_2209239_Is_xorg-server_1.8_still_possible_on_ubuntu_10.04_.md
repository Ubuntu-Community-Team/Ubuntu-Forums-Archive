---
title: "Is xorg-server 1.8 still possible on ubuntu 10.04 (lucid)"
date: 2014-03-04
forum: Desktop Environments
---

### Post by superkuh2 on 2014-03-04
Hi. For the last couple of years I've been encountering a growing number of Firefox browser induced crashes of my entire (fglrx) X 1.7.6 desktop on Ubuntu lucid. I'll be viewing some complex website in Firefox (versions 18 through 25) and quite suddenly my screen will go black for a second before I'm presented with a gdm login screen and session. The incidents are very easy to replicate.

For a long time I thought this was a manifestation of the X 1.7.6 pixmap crash ( X segfault in miCopyRegion / fbCopyNtoN ) referenced at [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/539772](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/539772) due to the similarity in my syslog messages correlated with the times of the crashes. But I compiled xorg-server-core 1.7.6 from apt-get source xserver-xorg-core and applied the suggested patches at,

[http://cgit.freedesktop.org/xorg/xserver/commit/?h=server-1.7-nominations&id=2c94da4e22520f4a3e783db06b73251131382868](http://cgit.freedesktop.org/xorg/xserver/commit/?h=server-1.7-nominations&id=2c94da4e22520f4a3e783db06b73251131382868)

I tested after successful installation and while it did make the suspect syslog error messages go away X still crashed. So I figure I need 1.8.

1.8 used to be available as a xorg-edgers PPA package for lucid. But those binaries seem to have been deleted from the site even though they once existed.  Ubuntu lucid X.org 1.8 ghost packages: [https://launchpad.net/~xorg-edgers/+archive/ppa/+build/1852863](https://launchpad.net/~xorg-edgers/+archive/ppa/+build/1852863)

So, my question, does anyone have access to these 1.8 binary packages for lucid anymore? Would they share them? 

Alternately I'll be trying to build 1.8 from source. I think this would be filled with pitfalls so I hope not to do it. Building source from Ubuntu repos is one thing and building from git is another. So links to actual guides or examples of compiling 1.8 from git for/on any version of ubuntu would be very much appreciated too. 

Thanks for your time. And yes, I know, I should upgrade to a supported version. I have my reasons.

---

### Post by phidia on 2014-03-04
Did you try [here]("http://xorg.freedesktop.org/archive/individual/xserver/")?

---

### Post by superkuh2 on 2014-03-05
> **phidia said:**
> Did you try [here]("http://xorg.freedesktop.org/archive/individual/xserver/")?  What you have linked to is the collection of archives of the source of xorg-server. I appreciate the gesture but acquiring the vanilla source of xorg-server is not a problem.   

My request was for anyone who may have downloaded the Ubuntu xorg-edger PPA binaries of xorg-server to share them. These binaries would be pre-customized and ready for the Ubuntu graphics stack, unlike any plain source archive. Alternately I asked for help finding examples of people who have compiled xorg-server themselves on ubuntu systems; such writing would include valuable information about configuration options for Ubuntu systems. The closest I have found is [http://edzeame.wordpress.com/2012/09/18/112/](http://edzeame.wordpress.com/2012/09/18/112/) while most pages link to the defunct [http://www.x.org/wiki/CompileXserverManually](http://www.x.org/wiki/CompileXserverManually) or non-debian/ubuntu specific [http://www.x.org/wiki/Development/BuildingX/?action=show&redirect=Development%2Fgit](http://www.x.org/wiki/Development/BuildingX/?action=show&redirect=Development%2Fgit) .

---

### Post by superkuh2 on 2014-03-14
So, it has been weeks or me trying and failing to compile the X stack and xorg-server 1.8. I became quite depressed as the X desktop crashes are starting to occur more and more frequently. I decided to try a complete distro upgrade and throw away my perfectly configured desktop. 

Unfortunately I cannot, because:

>An unresolvable problem occurred while calculating the upgrade:
>E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

And my list of "Broken" packages [http://pastebin.com/U9buaTaQ](http://pastebin.com/U9buaTaQ) is so proliferate that I cannot possibly see fixing it. So there's another reason I am stuck with ubuntu lucid.

Please, someone, anyone. This is driving my crazy. I've spent hundreds of hours trying to fix these crashes. Compiling my own X stack is infeasible for me (and most people). Upgrading my distro is damn near impossible. Someone out there has to have xorg-server 1.8 packages for lucid. They existed once. I know they existed.

If I cannot find a way I'm just going to wipe the entire thing and switch to debian.

---

### Post by Frogs Hair on 2014-03-15
You can add old repositories by inserting the code name of the release .[https://superuser.com/questions/339537/where-can-i-get-therepositories-for-old-ubuntu-versions](https://superuser.com/questions/339537/where-can-i-get-therepositories-for-old-ubuntu-versions)

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

