---
title: "Desktop is really slow."
date: 2006-08-12
forum: Desktop Environments
---

### Post by oxEz on 2006-08-12
Hi. I'm been using Linux for a while, and I decided I'll really give ubuntu a try this time (after some years using Gentoo).

After a fresh install, I did the usual stuff (software upgrades from repos, kernel upgrade (using k7, as I have an AMD Athlon XP 2600+). I then realized my desktop was not responsive as it was on slackware/gentoo. I browsed forums here, and some people said that using XGL on top of X could help to make the desktop run faster. So I did install XGL, tried it with and without compiz, it only made windows to move more smoothly, nothing more.

I then checked if DMA was on, and it is (for both of my hard drives, /dev/hda and /dev/hdb.).

I continued my research, and I saw that InitNG thing. I followed the how-to on the ubuntu wiki. It installed well, I configured my services in runlevels as I'm used to in gentoo; it only reduced boot/shutdown time. Desktop is still laggy.

So I'm asking to people out there, for hints that might help my desktop to be more responsive. Maybe I'm not clear enough when I say "responsive": Example, when I minimize a window, that little animation going on is *not* supposed to take 3 seconds to complete (It's not that it's slow in that case (ie: slow motion), but it's all scratchy, no smoothness). When I click the main menu, it's *not* supposed to take 2 seconds for it to pop up. And that is, when no other app is running. Also, scrolling pages (ie: ubuntu forums) in firefox is laggy. (It's worst when I'm running amaroK..)

I'll post my system specs, if it can help..

AMD Athlon XP 2600+
1GB of ram (DDR400)
nVidia GeForce 6600GT (drivers installed, and working.)
40GB Maxtor / 250GB Western Digital hard drives.
uname -a: Linux titan 2.6.15-26-k7 #1 SMP PREEMPT Thu Aug 3 03:40:32 UTC 2006 i686 GNU/Linux


Also, I'm uploading a snapshot of what 'ps aux' gives me, so you can have an idea of what's running on my system right now. Load averages are:  0.62, 0.56, 0.53.

Many thanks in advance!

---

### Post by oxEz on 2006-08-12
I'll try this: [http://www.ubuntuforums.org/showthread.php?t=189192](http://www.ubuntuforums.org/showthread.php?t=189192)

I'll update if there's anything.

---

### Post by oxEz on 2006-08-18
The solution for me was to reinstall Gentoo. It looks like it's the only distro that fits my needs, and the one I have no issue with ;)

---

