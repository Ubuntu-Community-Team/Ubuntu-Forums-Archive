---
title: "Trying to run Debian KDE, having problems..."
date: 2008-05-22
forum: Debian
---

### Post by SZF2001 on 2008-05-22
OK, so for one thing I'm trying to install ndiswrapper by source. This usually works out just fine in Debian with Gnome, but this seems to be having trouble. I usually just install build-essential off the install CD, use the terminal to find the ndiswrapper source folder, type 'make uninstall' 'make' 'make install', and I'm good to go. I keep getting this message:

> coledebkde:/home/coleman/ndiswrapper-1.52# make
make -C driver
make[1]: Entering directory `/home/coleman/ndiswrapper-1.52/driver'
Makefile:35: *** Cannot find kernel version in /lib/modules/2.6.18-6-686/build, is it configured?.  Stop.
make[1]: Leaving directory `/home/coleman/ndiswrapper-1.52/driver'
make: *** [all] Error 2

Alright fine, maybe my headers aren't updated or something. I mean after all this IS a fresh install. So let's go over to the KPackage manager with a land line.

Everything refreshes and oh goodie there are updates! But what's this? I have to install them one by one? I'll try pressing shift and selecting more than one package... No, I can't? Will CTRL and individual package clicking work? No... What the hell?

Wow. This package manager sucks. Oh well, I can get by. I guess I'll just go into Debian's official package search and pull up their ndiswrapper packages there, no problem.

Oh wait, there is a problem. .deb files refer back to KPackage manager. Fine I'll use this ungodly tool again to... What? Can't solve the dependencies? But these dependencies are on your repository, surely they can be installed!

They can. One by one. When you search for them individually. The good 'ol Synaptic of GNOME Debian would check your dependencies, then prompt you and ask if you want to install the package with the dependencies. Is that really something the KDE team couldn't implement?

Alright. So enough bickering, I'll just throw you guys the questions:

1 - Is there a way I can use dpkg in the terminal for it to actually search around the repositories and install dependencies for the .deb file I want to install? I can't even get Envy going.

2 - Is there a way to get the good Synaptic Package Manager of Debian GNOME onto this KDE version? Maybe it will actually check dependencies for me and, you know, be awesome.

3 - I have installed the latest of everything, and I am still getting that ndiswrapper error message. What can I possibly do?

Thanks in advance.

---

### Post by jdhore on 2008-05-22
1. "apt-get install whatever" is your friend. To fix dependencies from debs you manually installed, "apt-get -f install"

2. "apt-get install synaptic"

3. Try installing ndiswrapper from the repos.

---

