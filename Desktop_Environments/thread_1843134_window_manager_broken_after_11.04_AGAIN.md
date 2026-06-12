---
title: "window manager broken after 11.04 AGAIN"
date: 2011-09-12
forum: Desktop Environments
---

### Post by BloodyIron on 2011-09-12
Okay so I followed a whole plethora of instructions to fix my window manager after upgrading to 11.04.

I'm pretty sure the last thing which fixed it was getting the desktop manager to run compiz --replace on start, but now I can't find where I stashed that, the window manager is gone, and when I try to do it again in the terminal the screen blinks repeatedly until i log out or reboot the system.

Seriously guys, what the **** is up with 11.04?

Also, is there a thread covering this already? I have tried looking around, can't find one yet.

---

### Post by BloodyIron on 2011-09-13
Bump

---

### Post by MG&amp;TL on 2011-09-13
I had this problem in a different form, but it seems to be fixed for me in 11.10, so stick with 10.04 release and wait for 11.10, or get the beta.

EDIT: ahhh....mythubuntu....sorry...I have Ubuntu, scratch what I just said. I really should check those tags more often. Prevents embarrasments like these.

---

### Post by BloodyIron on 2011-09-13
> **MG&TL said:**
> I had this problem in a different form, but it seems to be fixed for me in 11.10, so stick with 10.04 release and wait for 11.10, or get the beta.

EDIT: ahhh....mythubuntu....sorry...I have Ubuntu, scratch what I just said. I really should check those tags more often. Prevents embarrasments like these.

lol, it's still useful information though :)

i'll just have to bide my time and figure out something else in the mean time

---

### Post by Blasphemist on 2011-09-13
Usually this happens when changing compiz settings that affect others. I know, it is not uncommon. I believe these are what you are looking for.
> How to Revert your changes in the event you end up breaking unity.

You can reset unity or compiz or both by doing the following.

Open a terminal by hitting ctrl+alt+t or alt+f2, if one of those key combination does not open the terminal try ctrl+alt+f1 thru f6. Then type this command in terminal to reset unity.
```
Unity --reset
```

Use these commands to reset all the settings in compiz.

```
gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
```
This came from this great tutorial that you may or may not be into. [http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

---

### Post by BloodyIron on 2011-09-13
> **Blasphemist said:**
> Usually this happens when changing compiz settings that affect others. I know, it is not uncommon. I believe these are what you are looking for.

This came from this great tutorial that you may or may not be into. [http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

I'm not using Unity, Mythbuntu uses XFCE because its lighter weight, is there an equivalent for XFCE?

---

### Post by BloodyIron on 2011-09-15
Guess not.

---

### Post by Blasphemist on 2011-09-15
If you're interested, I'm about to install natty in a test partition and then change it to use Enlightenment E17. I plan to keep track of what I do and how. If Xfce is giving you trouble on mythbuntu, maybe trying E17 is of interest to you. From what I can tell it can be done without removing what DE you're using.

Anyway, let me know if want made aware of how it goes.

---

### Post by BloodyIron on 2011-09-15
how lightweight is it compared to XFCE?

> **Blasphemist said:**
> If you're interested, I'm about to install natty in a test partition and then change it to use Enlightenment E17. I plan to keep track of what I do and how. If Xfce is giving you trouble on mythbuntu, maybe trying E17 is of interest to you. From what I can tell it can be done without removing what DE you're using.

Anyway, let me know if want made aware of how it goes.

---

### Post by Blasphemist on 2011-09-15
> **BloodyIron said:**
> how lightweight is it compared to XFCE?

I didn't quickly find any tests for this comparison. Here are the specs for Bodhi linux that uses Enlightenment E17. I don't know how much of that is required by E17.
300mhz i386 Processor
128megs of RAM
1.5g HD space

---

### Post by BloodyIron on 2011-09-15
That is probably sufficiently low, lol thanks :D

> **Blasphemist said:**
> I didn't quickly find any tests for this comparison. Here are the specs for Bodhi linux that uses Enlightenment E17. I don't know how much of that is required by E17.
300mhz i386 Processor
128megs of RAM
1.5g HD space

---

