---
title: "quake 2 and 3"
date: 2014-10-02
forum: Gaming &amp; Leisure
---

### Post by stedun on 2014-10-02
hiya everyone

can anyone tell me how i can install any quake version? i have the windows discs but am on ubuntu. which is great! 
i have found "yamagi.org"  but dont know how to install a "tarball" - is quake (any versions) avalable on the software thingy? 
i cant get my head round installing stuff on this platform. just from the software installer thing. 
thanks everyone!

---

### Post by oldrocker99 on 2014-10-02
Open a terminal and type this:
```
suao apt-get install quake3 synaptic
```
The info for the file says:

"This package contains a launcher script and menu entry to play
Quake III Arena with the ioQuake3 engine.

To make this package useful, you will need to create and install the
non-distributable quake3-data package, by using the game-data-packager
package. This requires pak0.pk3 from a Quake III installation or CD-ROM."

In other words, it looks like Quake3 is eminently playable as long as you copy that file to your system in such a way that the Linux quake3 program can find it.

**Synaptic**, by the way, which is not included in a standard installation, is just about the best package installer for you to use, with both a comprehensive Search and a Quick Filter button, and is much faster than the Ubuntu Software Center. The Software Center is great for purchasing software, but is pretty pokey otherwise, since it insists on installing each program when told, and queues up all the other programs until the one being downloaded is installed. Synaptic lets you check every program you want installed, until you click the Apply button, at which point it will download all the packages, and then install them. 

**Tarballs:**The standard way to distribute compressed files in Linux is as a tarball, that is, a .tar or a .tar.gz file. The difference is that a tar.gz file is more heavily compressed. If you open the directory where the tarball is located in a file manager, it can be opened just like a .zip file, with the archive manager your desktop comes with.

Good luck!

---

### Post by mastablasta on 2014-10-03
also usually tarballs include readme file explaining how to do the install.

avoid compiling form source - use trusted ppa and install scripts instead. makes life easier.

---

