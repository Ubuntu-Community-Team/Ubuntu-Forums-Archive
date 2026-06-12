---
title: "Fonts, xorg, CPU usage, and other issues"
date: 2008-04-28
forum: Desktop Environments
---

### Post by Gannin on 2008-04-28
I just upgraded from 7.04 to 8.04 by way of a clean install, and so far I'm experiencing some issues.  Everything below I tried with the default video driver, the nVidia driver provided by Ubuntu, and the beta nVidia driver downloaded and installed from nVidia's website.

First of all, the fonts are much worse than they've ever been.  Before, in 7.04, in order to get really nice-looking, clear fonts, I did "dpkg-reconfigure fontconfig-config" and set it to Autohinter and Automatic, and in Gnome I set the fonts to subpixel smoothing, as I have an LCD monitor.

I've tried the same settings in 8.04, and the fonts are much fuzzier than they should be.  No matter what combination of settings I use now, I simply can't get the fonts as clear as they were in 7.04.  This is especially true in the Gnome terminal, where the fonts are Super Fuzz of the Ninth Galaxy.

Speaking of the Gnome terminal, it's extraordinarily slow.  For lack of a better way to say it, when new text is added to the terminal, and when scrolling up and down in the terminal, it acts as though it's refreshing at about five frames-per-second, despite other graphical elements moving at their normal speeds.  The Gnome terminal used to be nice and speedy, so I have no clue why it's going so slow now.

My system is an AMD 64 X2 4400+, with 2 gigs of RAM and an nVidia GeForce 8600 GT card.

Also, xorg is constantly using 38% - 58% of one of my cores, even when idling, and when I use Gnome terminal, it uses 10% - 30% of the other core.

---

### Post by mannih2001 on 2008-04-28
When I updated to 8.04 on Friday, I first thought that fonts sucked really bad, too. Then I noticed the embarassing truth: I just had to press the auto-adjust button on my monitor. Everything was nice and sharp after that.

---

### Post by Gannin on 2008-04-28
All the other images are sharp and clear, it's only the fonts that are fuzzed out about the edges.

Considering my system was still clean, as I hadn't started installing my apps or anything, I decided to give Mandriva 2008.1 a spin for comparsion.  I still like Ubuntu the best and there are a lot of little things that bug me about Mandriva, but I have to say that the fonts in Mandriva are very sharp and very clear.  With everything going for Ubuntu, I wonder why they can't handle their fonts more like Mandriva, as in, I wonder why they haven't put in the time to make their font system better.  Not to mention the step backwards they took with the latest release.

---

### Post by peterdk on 2008-04-28
Yeah, I had the same issue, I really had lousy fonts. Going to look for other distro's, and that after 2 years of ubuntu..... They really took a big step backwards with this release.

---

### Post by Gannin on 2008-04-28
For the time being I've decided to use Mandriva 2008.1.  It's a decent alternative.  It has some good sides and some bad sides, but for me it just doesn't feel like home.

The good is that the desktop is a bit faster and more responsive because the entire system is compiled for i586 instead of i386, not just the kernel.  Also, when actually installing a package, they've gotten it to the point where installing a .rpm is faster than installing a .deb.  And most of all, the fonts are very nice... clear and crisp.  The system services editor is also quite nice and it actually lets you edit all the services on the system, not just a small list of them, forcing you to instead use a program like sysv-rc-conf like Ubuntu does, or do it manually.  Plus all the services have accompanying descriptions of what that service is.

The down side is that there are a lot of little bugs and rough spots which Mandriva tends to be famous for.  Some of the packages install some binaries in the wrong places and you have to update them manually.  Even though installing .rpms is faster than installing .debs, their package management system is awful.  This can be partially remedied by using the smart package manager, which is like Synaptic, instead of the built-in software and using easyurpmi to update the smart sources.

If you can get around the rough edges, Mandriva seems to be a smooth running system with very nice fonts.  I just wish they'd fix up Ubuntu so I can go back.

---

