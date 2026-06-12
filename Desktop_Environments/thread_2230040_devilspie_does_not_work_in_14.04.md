---
title: "devilspie does not work in 14.04"
date: 2014-06-16
forum: Desktop Environments
---

### Post by jchonig on 2014-06-16
I have been using devilspie for years to place windows on Xubuntu 12.04.  On Xubuntu 14.04 the first thing I noticed is that it is not getting notifications about most windows.

I tried xprop on a few windows and discovered that it exits without any output.  I'm not sure if they are in any way related.  If I install and switch to the Kubuntu 14.04 desktop xprop does work.

Anyone seen this behavior or know of an existing bug (I could not find one).

I don't remember for sure if devilspie or xprop worked on Unity or Gnome desktops, when I tried them it was the wee hours of the morning.  I think devillspie worked with Unity.  Neither of those handle multi-monitor (two separate screens) well so I gave up on them.

Thanks.

Jeff

---

### Post by squakie on 2014-06-17
Well, I had never heard of devilspie before, but after reading the description in the package manager I decided to try it.  Downloaded and installed fine in my xubuntu 14.04.  I created a .devilspie folder off my home folder and created a firefox.ds there as well.  What's interesting is that indeed it doesn't seem to be working, just as you mentioned.  It never puts firefox in a different workspace, I don't see any messages.  Since I loaded this to see if I could help you, I'll keep banging around on it and the net and see if I find some solution.

---

### Post by squakie on 2014-06-17
Ok, remembering that this is the first time using this for me, I may be asking a dumb question:  did you add the daemon startup to sSetings Manager/Session and Startup/Application Autostart ?

Had to click "Add" then put in a name and the executable as /usr/bin/devilspie .

Perhaps after you went to 14.04 the daemon startup was lost?

Mine works fine (well, a simple thing like starting Firefox in workspace 4 goes) now that I have the daemon being started.

I don't think that's your problem since you say you aren't getting notifications from all windows, however now that I have it installed, the daemon started, and a simple .ds file working, perhaps you could provide a sample of one of your .ds files that appears not to provide notifications and a brief description of what it does and what you expect as notification.  I can try to follow it and see if I can duplicate it.

---

### Post by squakie on 2014-06-17
I did see there is something called devilspie2 in the repositories - perhaps it might work better?

---

### Post by Elfy on 2014-06-17
I've been using devilspie in every version of everything that I've run since I started using it. It certainly worked in 14.04 and it's working now in 14.10.

Admittedly I use it only for a few programs, but it does work.

Examples of programs you're having issues with?

---

### Post by ufanan on 2014-11-10
Hi,

my problem is that devilspie apply rules to existing windows even if I don't use the "-a" flag, but then it does no apply to new windows.

I've tried in daemon and in interactive mode.

Using xubuntu-desktop over ubuntu (unity).

Any help?

---

