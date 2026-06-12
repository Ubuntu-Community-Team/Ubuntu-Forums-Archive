---
title: "Switching GCC"
date: 2005-10-25
forum: Desktop Environments
---

### Post by Kelsin on 2005-10-25
I'm going to be using Ogre3D as a engine for a project I'm working on. Currently the samples don't compile correctly in > GCC 4.0. They segfault at runtime. I'm able to fix the problem by installing gcc 3.4 and g++ 3.4, resetting the /usr/bin/gcc and /usr/bin/g++ symlinks and recompiling Ogre3D and it's samples.  Is this going to cause problems in my system? I can't compile programs with Orge on GCC 4, but I don't want to cause problems with my system (which I use for many other things) by doing this?

Any help would be appreciated :)
Thanks

---

### Post by LorenzoD on 2005-10-25
Instead of updating symlinks, why not just specify gcc-3.4 as your CC?

---

### Post by Kelsin on 2005-10-25
If that is the better way to do it, I'll do it that way, but regardless of the way that I specify to use 3.4 from now on, will that break anything in the system?

---

### Post by LorenzoD on 2005-10-25
It won't break anything you currently have, or any .debs that you install. Where you could have problems, is if you try to compile things that link to libs that were compiled using gcc-4.0.

---

### Post by Kelsin on 2005-10-25
[QUOTE=LorenzoD]It won't break anything you currently have, or any .debs that you install. Where you could have problems, is if you try to compile things that link to libs that were compiled using gcc-4.0.[/QUOTE]
Ok that makes sense!

Thanks a lot!

I think I'm getting help in the Ogre3D forms on a change I can make that allows me to compile with 4 :-) Hopefully that works! Still this was informative and very helpful.

Thanks

---

### Post by LorenzoD on 2005-10-25
I was also planning on trying to compile and debianize Ogre3D. If you get any useful tips that help you compile with gcc/g++ 4, let the rest of us know, won't you? :smile:

---

### Post by Kelsin on 2005-10-25
[QUOTE=LorenzoD]I was also planning on trying to compile and debianize Ogre3D. If you get any useful tips that help you compile with gcc/g++ 4, let the rest of us know, won't you? :smile:[/QUOTE]

Yep I just got it working!

All I did was download the .tar.gz version of Orge3d and made one small change:

You edit the last line of OgreMain/src/Makefile.am and get rid of the "-lW," and everything after that.

My last line is:

```

libOgreMain_la_LDFLAGS = $(SHARED_FLAGS) -version-info @OGREMAIN_VERSION_INFO@

```

Then you can compile with gcc 4.0 as normal:

```

./configure --with-platform=GLX
make
sudo make install

```

You do want to make sure to have all the packages you need. I did this by installing the ones on the website then during the install when it said it couldn't find some file, search that name in Synaptic, install the package and the -dev package and I was good to go.

On my desktop I have an NVidia 5700 as as the Orge3D wiki says I used the GLX platform (on the configure line up above). On my laptop I have a crappy intel motherboard graphics chip like thingy, and when I tried to use the default (which is SDL) I got no graphics at all... The programs seemed to run fine, no seg faults, but just black screens that exit when I hit escape as they should.

When I compile with the GLX option the demos run really slow, way too slow... I don't know exactly what the problem is, but will hopefully figure it out soon. Probably just my X settings for this laptop aren't quite up to speed. I assume it's just it being a horrible video card, but for all of the demos in Orge I can't get past 6 fps... kindof dissapointing. The card can play WoW in windows... so I assume it can do better then 6 fps when displaying one model.

Anyway... I'll have to figure that out at some point. Probably a configure setting for Ogre's ./configure

There you go though, that's the change that's needed for GCC 4 in Ubuntu at least :)

---

