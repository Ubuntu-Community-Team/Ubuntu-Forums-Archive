---
title: "Using apt-get on local .deb dile"
date: 2005-04-02
forum: Desktop Environments
---

### Post by mcollins on 2005-04-02
I like using apt-get to install programs. I just learned in the Debian manual that you can build a package from a .deb file, then run apt-get. I need a little help thought, let me catch you up:

I downloaded gtk-gnutella/gtk-gnutella_0.95.0-0_i386.deb, and saved it in a folder in /root called /debs. (/root/debs). In console while in the root directory, I then typed:  dpkg-scanpackages debs /dev/null | gzip > debs/Packages.gz. That "null" file is your override file, you can specify options in the package's control file like package, priority , and section. If you want to just use the default file, you use /dev/null. After running that command I'm left with Packages.gz in my /root/debs folder. Next I added the /root/debs folder to my source.list with this statement: deb file:/root debs/. Then I did an apt-get update. But when I apt-cache show gtk-gnutella, it's showing an old version off my universe repository. The whole purpose of this is to have the latest vesion.

Any ideas where I went wrong?

Matt

---

### Post by ubuntu_demon on 2005-04-02
a deb file is an installable file. If you want to install a .deb file you just have to do this :

sudo dpkg -i localfile.deb

You can also build .deb files from source. Then you have the latest software and you can remove it easily. I have used it once for amule. But on average it isn't worth the hassle. If you want newer packages just upgrade to hoary. If you really need to compile sources then install the packages build-essential and checkinstall

for upgrading to hoary go here :

[http://www.ubuntulinux.org/wiki/GuideToHoary](http://www.ubuntulinux.org/wiki/GuideToHoary)
[http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes](http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes)

if you've installed backports on your warty also go here :
[http://ubuntuforums.org/showthread.php?t=12174](http://ubuntuforums.org/showthread.php?t=12174)

---

### Post by mcollins on 2005-04-02
Well I like apt-get because it takes care of dependencies. And if those dependencies needed anything apt-get would take care of that too. And if you remove a package it knows to remove all those dependencies you no longer need. That's my understanding anyway!

But first I think I'll upgrade to Hoary like you said. I might even find the version of gnutella I want is there.  It sounds easy enough, just changing the sources.list and upgrading as usual.

Matt

[QUOTE=demon666_nl]a deb file is an installable file. If you want to install a .deb file you just have to do this :

sudo dpkg -i localfile.deb

You can also build .deb files from source. Then you have the latest software and you can remove it easily. I have used it once for amule. But on average it isn't worth the hassle. If you want newer packages just upgrade to hoary. If you really need to compile sources then install the packages build-essential and checkinstall

for upgrading to hoary go here :

[http://www.ubuntulinux.org/wiki/GuideToHoary](http://www.ubuntulinux.org/wiki/GuideToHoary)
[http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes](http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes)

if you've installed backports on your warty also go here :
[http://ubuntuforums.org/showthread.php?t=12174](http://ubuntuforums.org/showthread.php?t=12174)[/QUOTE]

---

### Post by ubuntu_demon on 2005-04-03
the version from gtk-gnutella is : 0.95-2ubuntu2

apt-get is a front-end to dpkg. So if you install something with apt-get dpkg is called. So installing a package with dpkg is essentially the same as installing with apt-get.  As far as I know there isn't an apt-get command which installs a local .deb file so you have to you dpkg like  I mentioned.(and yes apt-get and dpkg resolve dependencies needed if it is not too complicated)

Upgrading to hoary is indeed easy. But you have to do it the right way. If you have backports installed you have to do it in the way explained here :
[http://ubuntuforums.org/showthread.php?t=12174](http://ubuntuforums.org/showthread.php?t=12174)

step 9 isn't necessary and I wouldn't recommend myself it until hoary gets released.

---

### Post by mcollins on 2005-04-04
This is straight from the Debian Manual, Section 2.2: [http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages)
When you run that dpkg-scanpackages command, you end up with a .gz file. And if you view it, it lists the file details just like apt-cache show does. Add the folder where that .gz file is to your repository list, and supposedly you can run apt-get install on it.

[QUOTE=demon666_nl]the version from gtk-gnutella is : 0.95-2ubuntu2
As far as I know there isn't an apt-get command which installs a local .deb file so you have to you dpkg like  I mentioned.(and yes apt-get and dpkg resolve dependencies needed if it is not too complicated[/QUOTE]

---

### Post by ubuntu_demon on 2005-04-04
This part of the manual is not ment for you but for serious nerds and packagers :). It could be handy if you need to install a lot of .deb files. 

To install only one or a couple of packagea please use dpkg -i as I explained earlier.

but thnx to this easy manual I was able to help someone else who did need this command see :

[http://www.ubuntuforums.org/showthread.php?t=23843](http://www.ubuntuforums.org/showthread.php?t=23843)

---

