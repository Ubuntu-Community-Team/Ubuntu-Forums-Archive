---
title: "High X CPU usage when using KDE programs (10.04)"
date: 2010-05-12
forum: Desktop Environments
---

### Post by gsteinert on 2010-05-12
I have recently upgraded from Kubuntu 9.10 to 10.04. I am having trouble with CPU usage by the X server. 

When running KDE programs (for example Kontact and Amarok) my computer is becoming very sluggish. This seems to be because X is using 90-100% of the CPU constantly when there are any changes to the application (any sort of redraw, even the mouse moving across the screen). I don't experience this with other applications (I am currently writing this from Chromium with no issues at all).

Below is all the relevant information I can think to include.

INSTALL PROCESS:
Fresh install from Ubuntu 10.04 LiveCD. My /home direrctory is on a separate partition so that has remained unchanged from 9.10. After installing Ubuntu, I installed the kubuntu-desktop package to install kdm and the KDE desktop.

The only real change from my last install is that /var is now also a separate partition (in a bid to save my MySQL data should I have to reinstall again) but it is on the same hard drive as my root partition and so shouldn't be causing any performance issues.

MY X SETUP:
Three screen setup using onboard and PCI graphics cards. This worked perfectly before and, after reconfiguring X using nvidia-xconfig works almost as well again. Except that one of my monitors autodetects at 1280x1024 where before it was a higher (and widescreen) resolution.

The issue only presents itself when KDE application screens are visible and disappears when they are hidden (either minimised or closed) As far as Ican tell it could be an X, Qt or KDE issue. But I am not sure what versions of these will have been changed in the upgrade.

Hoping someone can help,

Gary

---

### Post by gled on 2010-05-27
Hi, 

I'm having the same issue, same install method but 3 graphic cards ( 2*nvidia 6200 PCI and 1 nvidia 210 PCIE ).

X won't even start with the 210 configured, but when I configure the 2 6200 ( using nvidia-settings ) it boot ok with 4 screens.

It's just that X stays at 100% cpu ( and even more when it can ), which makes the box unresponsive.

The only workaround I found was to install a debian 5, which works really good with my setup, and do things on hand.

I noticed also that when not using NvAgp "1" , after some time, the box freeze and a hard reset is needed...

No news from guys from launchpad, nothing :/

---

