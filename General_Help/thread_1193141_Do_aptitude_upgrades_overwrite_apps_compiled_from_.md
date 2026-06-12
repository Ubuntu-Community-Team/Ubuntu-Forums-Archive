---
title: "Do aptitude upgrades overwrite apps compiled from source?"
date: 2009-06-21
forum: General Help
---

### Post by infinitejones on 2009-06-21
Can't work out how to word the question properly so here's the scenario:

I've downloaded the source code of mplayer so that I can compile it with support for encoding x264. That's all gone fine and my PC is happily encoding x264 as we speak.

However, previously I'd been using the mplayer/mencoder from medibuntu, updating it automatically with aptitude etc. So what happens next time the medibuntu repository updates their mencoder debs? 

Will Ubuntu assume that my current version of mencoder is out of date and upgrade it? And if so, will it maintain the ability to encode x264, or will I have to download and compile from source again?

---

### Post by KeyserSoze93 on 2009-06-21
They shouldn't do, since most makefiles put the bin in /usr/local/bin rather than /usr/bin.

If you want to check, just run:
```
which app
```
where app is your app, and you should get an a message saying where the bin is getting called from.

Also, /usr/local/bin should be before /usr/bin in your path, so the new version in /usr/bin will simply never get called.

---

### Post by jacksaff on 2009-06-21
If you don't want apt to upgrade a package you can use apt to 'pin' it. Synaptic has a gui to do this.

---

### Post by infinitejones on 2009-06-21
Great, thanks, both useful answers.

But let's say I've installed version 0.5 of something via aptitude, then I also compile it from source too for some reason. Then version 0.6 comes out, which fixes a security issue in 0.5. Aptitude will update the version I installed from a repository, but it sounds like I'd still be defaulting to the older version I compiled myself every time I used it.

Is that right? It sounds like I'd need to be keeping track of every application I compiled from source and updating it manually.

Is it just one of the trade-offs of using a package management system?

---

### Post by andrew.46 on 2009-06-21
Hi infinitejones,

> **infinitejones said:**
> It sounds like I'd need to be keeping track of every application I compiled from source and updating it manually.

Is it just one of the trade-offs of using a package management system

There is a middle way :-). Have a look at using checkinstall and manipulating two of the checkinstall options: --pkgname and --pkgversion. The Ubuntu package management system will respect these 2 settings and if the *pkgversion* demonstrates a higher version number than the repository version number your local copy will not be overwritten.

All the best,

Andrew

---

