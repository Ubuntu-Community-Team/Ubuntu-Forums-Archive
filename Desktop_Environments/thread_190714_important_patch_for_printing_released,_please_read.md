---
title: "important patch for printing released, please read on"
date: 2006-06-06
forum: Desktop Environments
---

### Post by garba on 2006-06-06
Hello folks, Pascal De Vuyst has just come up with a nice patch for libgnomeprint which aims at fixing some of the nasty issues with the printing dialog in gnome, please take out a few minutes of your time and give it a try, you can find it here:

[https://launchpad.net/bugs/34112](https://launchpad.net/bugs/34112)

---

### Post by garba on 2006-06-06
here are the patched debs

---

### Post by felipe_alfaro on 2006-06-06
Could you just post the source .deb package? I'm running Ubuntu on PPC :-)

---

### Post by garba on 2006-06-06
applying the patch and building the deb is quite trivial:

apt-get source libgnomeprint
sudo apt-get build-dep libgnomeprint
chdir to libgnomeprint(whatever it's called)
move the patch file over to <packagedir>/debian/patches
and then run fakeroot dpkg-buildpackage

that's all there's to it, hope this helps 8)

---

### Post by timetunnel on 2006-06-06
The debs fixed the bug on my system, but there's a little issue with them regarding updates: after installing them the ubuntu update manager thinks the packages for libgnomeprint in the respositories of Dapper are newer and offers me to update to them (which would mean to revert to the original packages).

Jens

---

### Post by garba on 2006-06-06
[QUOTE=timetunnel]The debs fixed the bug on my system, but there's a little issue with them regarding updates: after installing them the ubuntu update manager thinks the packages for libgnomeprint in the respositories of Dapper are newer and offers me to update to them (which would mean to revert to the original packages).

Jens[/QUOTE]

yep i know but i'd rather not mess around with the revision number, that would cause conflicts with an official update, which i hope will be coming soon

---

### Post by timetunnel on 2006-06-06
Ok. Sounds reasonable. Many thanks for the debs, Dapper is perfect now. :p 

Jens

---

### Post by interse on 2006-06-06
Thank you for the patch and instructions.  I now have the    libgnomeprint.tar.bz2 on my desktop.  The instructions which you posted are not quite clear, at least to me.

2nd line:  sudo apt-get build-dep libgnomeprint        Is this correct?  or should it be
        "build-deb"

4th line:  move the patch file over to <packagedir>/debian/patches and then run fakeroot dpkg-buildpackage.     

    Am I correct in concluding that the command is   "fakeroot dpkg-buildpackage"  ?

I realize that these are newbie-type questions, but I am still fairly ignorant of linux terminal commands.

---

### Post by mannheim on 2006-06-06
[QUOTE=interse]Thank you for the patch and instructions.  I now have the    libgnomeprint.tar.bz2 on my desktop.  The instructions which you posted are not quite clear, at least to me.

2nd line:  sudo apt-get build-dep libgnomeprint        Is this correct?.[/QUOTE]

interse: those instructions from garba were directed at felipe_alfaro, who wants to build the binary packages (the .deb files) from the source code. The file libgnomeprint.tar.bz2 is an archive which already contains the .deb files, so you don't need to do that stuff. You need to do:

```

tar -xf libgnomeprint.tar.bz2             [COLOR="Blue"]# unpack the archive[/COLOR]
sudo dpkg -i libgnomeprint2.2-*.deb  [COLOR="Blue"]# install all the .deb files
[/COLOR]
```

It is likely that this fix, or an alternative fix, will make its way into the dapper-update repositories eventually. So, if you don't really need it, you could just wait. Of course, we don't know when "eventually" will be ...

---

### Post by interse on 2006-06-06
Thanks mannheim.  I thought that the instructions given were a bit unusual.  Good to know that my professed ignorance was less extensive than I had thought.

---

