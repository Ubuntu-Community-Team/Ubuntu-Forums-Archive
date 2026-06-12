---
title: "How to make an ubuntu package"
date: 2006-03-06
forum: Desktop Environments
---

### Post by MichaelZ on 2006-03-06
Hello,

I would like to do an ubuntu package of an application I have recently compiled. In Windows, it would be to zip the application folder with the corresponding DLLs, so that a user has just to unzip it and use it. I have had a look at some links on how to do package, but they are a bit too difficult for me to understand (I am still newbie). And I am not sure that just zip the application repository in ubuntu would do the work.

Does someone of you know some easy tutorials and or way to make a package for re-distribution?

Thank you very much.

Best wishes,
Michael

---

### Post by az on 2006-03-06
It's not an easy thing.

You can use checkinstalll to make a rudementary package, but don't expect that package to work on an other machine.

Here are some references:
[https://wiki.ubuntu.com/HowToBuildDebianPackagesFromScratch](https://wiki.ubuntu.com/HowToBuildDebianPackagesFromScratch)
[https://wiki.ubuntu.com/MOTU/Packages/New](https://wiki.ubuntu.com/MOTU/Packages/New)
[https://wiki.ubuntu.com/MOTU/Packages/New/HowTo?highlight=%28MOTU%2FPackages%2FPackaging%29](https://wiki.ubuntu.com/MOTU/Packages/New/HowTo?highlight=%28MOTU%2FPackages%2FPackaging%29)
[https://wiki.ubuntu.com/DeveloperResources](https://wiki.ubuntu.com/DeveloperResources)

---

### Post by MichaelZ on 2006-03-06
Thank you very much :) . I will read the link you provide.

The application in question, just make use wxGTK2 and wx-common packages provided by ubuntu (though you have to install them). If I simply zip the folder containing the application (and its .so files), then a user that will unzip the application package and install the ubuntu packages (if necessary), would she/he be able to run it?

Thank you very much.

Best wishes,
Michael

---

### Post by Xian on 2006-03-06
[QUOTE=MichaelZ]If I simply zip the folder containing the application (and its .so files), then a user that will unzip the application package and install the ubuntu packages (if necessary), would she/he be able to run it?[/QUOTE]

That will work if you have installed the package in a build directory, which is to say not on your system but in a folder that includes all the paths where it would have been installed. Then tar that up and when it is untarred it should be usable on their machine.

---

### Post by MichaelZ on 2006-03-06
Thank you very much for your reply :).

The application is located in */home/michael/devel/CodeBlocks*, so your suggestion should work. I will give it a try.

Best wishes,
Michael

---

### Post by az on 2006-03-06
Unless you want to make a one-shot deal that will become obsolete in a few months, you should try to make use of shared-libraries.

There is no common API - there are different ways that applications talk to each other in Unix and what is statically-built and working now may not work in a few months.

The biggest strength of Ubuntu is that it is free-libre software.  That means that the development of the software is done collaboratively.  Programs interface with one another at the source code level.  That's why something distributed for another linux distribution may not work on a different linux distribution.  It would work, however, if you got the source code and compiled it for your distro using your distro's toolchain and shared libraries (they have differen versions, nothing more).

There are many advantages to this - the user get a choice in how to do things.  There are also many security advantages to centralised repositories with all the code being public.  

That's the limitations of just making an archive of the app you compiled for distribution - it may not always be banary-compatible with your OS.

A deb package is just an archive, but with a list of dependancies and pre and post install and removal scripts.  The package manager will try to resolve the dependancies of the shared libraries and other packages before installing the application.

---

### Post by MichaelZ on 2006-03-06
Hello,

Thank you very much for your useful explanations :D. 

My intention was to provide ubuntu users, a compiled version of the open source CodeBlocks IDE ([www.codeblocks.org](www.codeblocks.org)). This IDE makes use of shared libraries and not static one. Moreover, it is WIP and each day, there are bug fixes and new features. Therefore, a package done today would be "obsolete" tomorrow.

As I am still learning ubuntu (and Linux in general), I was searching for an easy way to provide such binaries. Later, possibly, a package :).

Best wishes,
Michael

---

### Post by az on 2006-03-06
[QUOTE=MichaelZ]As I am still learning ubuntu (and Linux in general), I was searching for an easy way to provide such binaries. Later, possibly, a package :).

Best wishes,
Michael[/QUOTE]


[http://forums.codeblocks.org/index.php?topic=1194.0](http://forums.codeblocks.org/index.php?topic=1194.0)

You have been beaten to it.
I gather the codeblocks community is looking to provide formal binary packages for the major linux distributions.

---

### Post by MichaelZ on 2006-03-06
[QUOTE=azz][http://forums.codeblocks.org/index.php?topic=1194.0](http://forums.codeblocks.org/index.php?topic=1194.0)

You have been beaten to it.
I gather the codeblocks community is looking to provide formal binary packages for the major linux distributions.[/QUOTE]

Hello,

Thank you, but I am aware of this as I am quite active member of CodeBlocks forum :). The admins/devs have decided to provide unofficially binary snapshots called nightly builds. But this only for Windows. Have a look at here:

[http://forums.codeblocks.org/index.php?board=20.0](http://forums.codeblocks.org/index.php?board=20.0)

Recently, a build for ubuntu 64bit is provided, even if not each night.

There are ongoing discussions about providing Linux nightly builds together with windows ones. For what I know, the responsible for the windows nightly builds would provide builds for Suse/Mandriva/Fedora, but not for ubuntu. Therefore, I would like to provide builds for ubuntu :). Anyway, I still have to learn a bit more about ubuntu and Linux in general.

Best wishes,
Michael

---

### Post by MichaelZ on 2006-03-07
Hello,

I have just remarked that the application I would like to package has a debian directory which should make it "easy" to create a .deb package.

I am not sure about the exact command I have to use. After a bit of research, I think that this should be the good one:

> 
sudo dpkg-buildpackage -rfakeroot -b


Can someone confirm if it is correct?

Thank you very much.

Best wishes,
Michael

---

