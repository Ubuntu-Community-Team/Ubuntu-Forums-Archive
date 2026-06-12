---
title: "GoogleEarth 5, 9.0.4 Freezup, Radeon X1550"
date: 2009-05-09
forum: General Help
---

### Post by Hudson78 on 2009-05-09
Yesterday I erased the Ubuntu 8.x partition on my hard drive and installed 9.04. 

Everything has worked well, with one minor and one major problem.

I mention the [_minor problem_]("http://ubuntuforums.org/showthread.php?t=1153327") because it *might* be related to the major problem.  The minor problem is that my Pointer shows a graphical artifact underneath it.  However, it is not consistent.  Sometimes it vanishes completely, only to reappear after logging back in or switching to another application.  This is a minor problem, merely an annoyance.

The "major" problem is that I have not been able to get GoogleEarth 5 to run, even though it ran perfectly well on 8.1.

I can install GE successfully.  When I launch it, the splash screen shows, the GE main window appears and the application begins to zoom into a 3D image of Earth as expected. Then, the Tips window appears (by default) and this is the first sign of a problem.  The right half of the Tips window is overlaid with the 3D earth graphic window.  Nonetheless, the app continues to zoom into Earth and very soon freezes completely.  Most of the time, all of Ubuntu freezes.  The Pointer will not respond, and I cannot ssh into the machine.  The entire OS appears to be dead. I have to use the power button to shut the machine down.

I've perused the Log viewer looking for a hint of the problem, but I haven't found anything hints. (I have not checked every log, though.)

*Many* people have had problems with GE5 on 9.04 and the solution for most has been to **rename one or more of the libcrypto or libssl files in the GE directory**.  Unfortunately, none of these solutions works for me.

My graphics card is a Radeon X1550 RV516 and I am using the Ubuntu-provided Radeon driver. (Not fglrx.)

The [_Radeon Driver page_]("https://help.ubuntu.com/community/RadeonDriver") seems to say that my card should be supported.  At least it says "...all these cards and derivatives have good 3D acceleration support..." and then it lists this card:

X1300 / R515 based cards

This is what lspci says about my card:

"02:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series] [1002:7183]"

The Xorg.conf file is empty; I think that is normal for my configuration.

I've tried the Mediabuntu package, but I experience the same problem.

I'm mystified by this problem. Does anyone have any ideas on how I might get GE 5 working on my Ubuntu machine?

Thanks in advance for any help.

---

### Post by Hudson78 on 2009-05-11
> **Hudson78 said:**
> Yesterday I erased the Ubuntu 8.x partition on my hard drive and installed 9.04.

...

The "major" problem is that I have not been able to get GoogleEarth 5 to run, even though it ran perfectly well on 8.1.

...

My graphics card is a Radeon X1550 RV516 and I am using the Ubuntu-provided Radeon driver. (Not fglrx.)

The [_Radeon Driver page_]("https://help.ubuntu.com/community/RadeonDriver") seems to say that my card should be supported.  At least it says "...all these cards and derivatives have good 3D acceleration support..." and then it lists this card:

X1300 / R515 based cards

This is what lspci says about my card:

"02:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series] [1002:7183]"



I don't think my graphics card is supported by the Radeon driver included in 9.04.  And, the current fglrx proprietary driver doesn't support my card any more either.

Since other issues have come up (besides GE5 and the Pointer issue), I've wound up just downgrading to 8.1, re-enabling the proprietary ATI driver, and turning off Visual Effects.

Now, everything seems to be working fine.

Most likely, I will just have to eventually dish out some bucks for a more modern graphics card.

---

