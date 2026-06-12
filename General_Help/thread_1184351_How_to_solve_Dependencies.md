---
title: "How to solve Dependencies?"
date: 2009-06-11
forum: General Help
---

### Post by ethoxyethaan on 2009-06-11
hello world, 

I have a problem with dependencies allow me to explain why:

Ive compiled: "ffmpeg, mplayer, vlc, gnome-mplayer, x264, anjuta, pidgin and transmission" from source and as a result i did not install the Actual packages from the ubuntu rep's.

Now whenever i want to install applications that depend on the corresponded packages it will ask me to install those, but i don't want to give in to that idea. even if i force to ignore dependencies it will still nag about it and Update manager will not function untill i fix the dependencies.

however my programs work perfectly, I've used the standard configure options for debian during compilation and installed the binaries / documentations in the same folders as it would normally do with the ubuntu packages.

I found out that one way to solve this is to install the packages first from the Rep's THEN overwrite those files with "make install", However i feel this is a rather messy solution. 

My question is: "How do i make my own .Deb packages and how do i tell aptitude to shut up about so called 'missing' dependencies, where can i find a detailed guide on how to make them and is it possible to install "dummy" .deb's to resolve dependencies.

---

### Post by nikgare on 2009-06-11
Have a look at **checkinstall**  - you run it instead of make install and it creates a deb for you.

---

### Post by jacksaff on 2009-06-11
Use checkinstall instead of make install when you compile your apps. It makes .debs out of your compiled programs and installs them for you. Then apt will know about them.

---

### Post by andrew.46 on 2009-06-11
Hi ethoxyethaan,

> **ethoxyethaan said:**
> My question is: "How do i make my own .Deb packages and how do i tell aptitude to shut up about so called 'missing' dependencies, where can i find a detailed guide on how to make them and is it possible to install "dummy" .deb's to resolve dependencies.

I guess the *real* solution is to learn how to make a formal debian package although having said that I have never actually bothered to do this myself :-). You can trick the repository with checkinstall and some naming conventions. For example I routinely compile the svn MPlayer and the following checkinstall line satisfies the repository that my version is newer:

```

$ sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
--pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
**[COLOR="Purple"]--pkgversion "3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2[/COLOR]**`"

```

and solves more than a few dependency problems. The key options here are *--pkgname* and *--pkgversion*.

Andrew

---

