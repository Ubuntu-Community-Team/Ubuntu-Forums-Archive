---
title: "[SOLVED] Quake2 freezes end of 1st chapter"
date: 2008-02-01
forum: Gaming &amp; Leisure
---

### Post by themacmeister on 2008-02-01
I don't know what's going on. I have the full original commercial QuakeII CD-ROM, and can install the entire game on many distros, and they all play through perfectly until the end of the first chapter.

It is here where I cannot continue. The message indicator comes up saying complete - and there are those annoying animated flying robots in the background - but no matter what I press/click, I cannot get myself off this screen (and onto the next chapter). I believe the server has reset, or has a new IP (0.0.0.0?), but no matter what I try - I am stuck one chapter in (and I'm sure there are many more).

Does anyone know a method of skipping to the next level. I am relatively comfortable with the console, so if it is something like 'Set +NextLevel' or something, I will be very happy. I have looked all over with no real help on QuakeII console commands.

Any help appreciated.

---

### Post by themacmeister on 2008-02-02
Bump - on an unrelated note, the problems I was having with Abuse.sdl were solved by building my own binary - the last 6 distros I have tried, the mouse would not work on the left side of the player (ie. it only worked at 45 degree angles - making the game unplayable.)

It now works perfectly!

Anyone know how to skip to the next level (or map) from the console in Quake II?

---

### Post by Brebs on 2008-02-03
quake2 - which engine? [qudos](ftp://brebs.me.uk/archlinux/abs/qudos-svn/) and [kmquake2](ftp://brebs.me.uk/fedora/9/) are much more "evolved" than the original.

---

### Post by DoktorSeven on 2008-02-03
I've seen that behavior with a few engines, and don't know why it's happening.  Best to go with one of the engines recommended by **Brebs**.

However, on a related note, I love Qudos, but I get a crash every single time on the first "mission"'s secret level at the door going into the room with the super shotgun on singleplayer, and occasionally (randomly) on multiplayer.  Need to try other engines, I guess.

---

### Post by Brebs on 2008-02-03
Try qudos from subversion, rather than qudos-0.40.1 - it includes some miscellaneous fixes.

---

### Post by themacmeister on 2008-02-05
Thanks heaps - I will give them a try - I thought I was using io-quake2 engine, as it looks pretty sweet, although the shortcut to start the game is quake2, with no icculus.org reference at all.

hmmm, an ArchLinux tarball for Ubuntu - should be fun :)

---

### Post by themacmeister on 2008-02-05
I was lucky enough to find the original Quake I on CD (must be rare!), and I got the GoTY version of Quake III Arena/Team Arena.

I am using FuhQuake for Q1
I am using io-quake3 for Q3A/Q3TA

I will either use Qudos or EGL for Quake II (I managed to download the SVN QuDos as a tarball).

Many thanks for your replies - if this works, I will post a success message - and close this thread.

---

### Post by Brebs on 2008-02-05
In the links I gave, click on "PKGBUILD". That gives major hints as to how to download and compile the program, on any distro ;)

---

### Post by themacmeister on 2008-02-06
I managed to build QuDos from SVN tarball from SVN website. Had to edit the Makefile to get original (ie: Quake II) support - otherwise, it kept complaining about gamei386.so missing... something to remember!

I have played through the first few chapters, currently on 3rd -

MANY THANKS to Brebs and DoktorSeven!

PS. It is blindingly slow with all options turned on (15fps on GeForce 7600GT). I have turned off everything except water transparency, and it is running smoother :)

---

### Post by Brebs on 2008-02-06
Look again at my PKGBUILD file. Note its multi-line make, and its copying.

You do not need to edit the Makefile. Simply build and copy the .so files, as in my PKGBUILD.

---

### Post by themacmeister on 2008-02-10
Sorry Brebs - I looked at the other two files, but not PKGBUILD.

Since I have already downloaded the same SVN source - can I use that makefile to build a faster(?) version. If not I might stick with the one I have.

Brebs, are you using OpenGL or SDLGL? Is there a difference in performance?

PS. I *will* have a look at the pkgbuild file tho...

EDIT: Pkgbuild looks identical to my build setup - nothing new - I will stick with current (buggy) build. The /dev/dsp busy message is horrible :P

---

### Post by Brebs on 2008-02-10
I haven't noticed a difference in performance (but then, I've got a fast PC anyway). I just use opengl because, as I wrote:
```
# Favours OpenGL over SDL - it does not lose focus when audacious/xmms starts.
```

---

