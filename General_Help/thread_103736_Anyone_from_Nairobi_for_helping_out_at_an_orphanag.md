---
title: "Anyone from Nairobi for helping out at an orphanage?"
date: 2005-12-14
forum: General Help
---

### Post by JackD on 2005-12-14
I'm spending some time over Christmas break in Nairobi, at an orphanage for AIDS children ([http://www.nyumbani.org)](http://www.nyumbani.org)). It's a terrific organization, it was founded by my wife's uncle, a Jesuit, about 10 years ago.

Anyway, they have 25 Dell Optiplex GXA computers (PII 233 MHz, 256 M RAM, 4 G HD, w/NIC) and Edubuntu *might *work just fine. My Linux skills are modest (I do support Linux installs for some IBM products like Domino and DB2). I have done the server install and apt-upgrade to Xubuntu. Then I have a barebones install that lacks all the packages on Edubuntu. If I want to pull off TuxTyping from Edubuntu and install it with dpkg, then I'm told of all the missing libraries.

They are getting a lot of push to go with a Windows solution,which I believe is well-intentioned, but will put them on the wrong track for their needs (educational and cost). I'm trying to get up to speed on all the facets of Ubuntu, but I just don't have time and am concerned that if there are no local resources for Linux (there are windows tech resources), then they will be running Windows 98.

You can email me at [email]jack@leadershipbynumbers.com[/email], if you have more questions or solutions.

Thanks

---

### Post by az on 2005-12-14
If you install the base system (server option) and then install xubuntu, you should add the edubuntu cd to the list of repositories 

sudo apt-cdrom add
(and insert the edubuntu cd for it to read the list of packages)


and do

apt-get install tuxtyping

apt will get the package along with all the dependancies.

---

### Post by JackD on 2005-12-14
Terrific, I'll do it tomorrow and let you know. Your tip makes it seem so easy to pull from a CD, but I guess the appeal of apt is get everything on-line. I just didn't know it could be done.

So, if I was to burn a bunch of ubuntu .deb packages to a CD, then it's possible to use apt to install it (of course, I need to make sure that I have all the libraries, etc.)

Is there a specific way to structure .deb files on a CD for apt to read?

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=3dchess&version=breezy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=3dchess&version=breezy&arch=i386)

Thanks, very much.

---

### Post by az on 2005-12-14
[QUOTE=JackD]
So, if I was to burn a bunch of ubuntu .deb packages to a CD, then it's possible to use apt to install it (of course, I need to make sure that I have all the libraries, etc.)

Is there a specific way to structure .deb files on a CD for apt to read?
Thanks, very much.[/QUOTE]

Yes, there is.

To sum it up, if you compiled everything from source code, you would get all the bits you needed to build all the applications and build them together and they would work fine.  

But this is not what you do by installing a linux distribution(usually).   Since these are precompiled binary packages, they have dependancies.  One package needs another package to work.  A package made for one version of one distro may not (will not) work with another verion of the same or another distro.  

The reason everything is split up is that many packages may share the need for one package, so there is no need for several copies of that package to be installed.

Years ago, screwing up your system by breaking dependancies was called RPM hell.  (RPM is another kind of package).  Ubuntu uses debian packaging which is called apt.  Apt installs debs.  Synaptic uses apt.

To make a debian package, you have to be very meticulous.  The dependancy and other compatibilities are complex, but some very very smart people do this so "it just works"  You also get security updates this way.

...except if you are not on the net.

All software in Ubuntu is installed from repositories.  Repositores are bunches of packages stored together, usually on the net.  A cd can be a repository.

A cd repository has to have a certain structure.  If you install Ubuntu on your broadband-connected box and ask it to install a bunch of software, it will download all the packages and their dependancies for you.  You can make a cd repository out of those downloaded packages to tak to a non-connected machine.

Here are the instructions:
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)


Packages are signed cryptographically, so that you know that it came from the source it says it came from.  An official Ubuntu cd full of package will install on your system just fine.  A custom cd like the one you can make will not have such a signature, so it will ask you to install the packages without authentification.  Since you did it yourself and got that packages from offical sources, you can safely say yes.


Please let me know if you need me to elaborate on anything.

Probably, if you install a default breezy setup on a machine with a cd burner and enable the universe (and other repositories) and installed everything you could possibly imagine you would need, you can make yourself a nice little custom cd repository to take with you to Africa.

---

