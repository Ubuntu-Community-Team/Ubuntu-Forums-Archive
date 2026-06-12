---
title: "penguin-command crashes in KDE 3.5"
date: 2006-02-08
forum: Gaming &amp; Leisure
---

### Post by MethodOne on 2006-02-08
When I start penguin-command (Missile Command clone in universe) in KDE 3.5, the resolution lowers and only a corner of the screen.  Here's the terminal output:

```
** Starting SDL init **
** Init video **
** Init timer **
** Loading Icon **
** Finding Joysticks **
** Init joystick **
** Loading Title Screen **
** Loading Sounds **
** Opening Audio Mixer **
   8 channels allocated
** Loading Music **
** Loading Sounds **
** Playing Music **
** Ready to enter Menu **
** Fade in Music **
** Showing Title Screen **
** Blit Background **
** Background image drawn **
** Loading Font **
** Init Font **
** Loading Images **
*** glibc detected *** malloc(): memory corruption: 0x0826d6f0 ***
```

My temporary fix to this problem is to run it in windowed mode twice.  This game works fine in GNOME 2.12.  I started out with regular Ubuntu (GNOME) and installed KDE later on.  My video card is a 8MB NVIDIA Vanta with the legacy drivers.

Edit:  This is actually a bug in the program itself.  I actually tried same version in breezy's universe on other distros and get the same result.  By installing the version in hoary, I fixed the problem.

---

