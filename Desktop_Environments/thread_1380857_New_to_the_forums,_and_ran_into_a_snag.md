---
title: "New to the forums, and ran into a snag"
date: 2010-01-14
forum: Desktop Environments
---

### Post by JiuJitsu500 on 2010-01-14
I've ran into a snag and was wondering if anyone could help... I downloaded through the synaptic manager KDE and XFCE desktops.... and cannot for the life of me figure out how to separate their startup programs (all programs start up on all three, not just the ones I want for individual environments).

Somehwat noobie alert, by the way....

So here are my issues, and I will gladly attempt to help anyone out I can here too with what I've figured out if I can.

- I want Cairo Dock to run on startup in GNOME only, I can't seem to find how to get it off the others while leaving it in Gnome (I am new to KDE and XFCE, please excuse my ignorance)

- The Grub splash screen is the Kubuntu version, and I'd rather have none again. A big white screen comes up as well right before the logon screen comes up, after the initial splash. When I open a terminal (ctrl, alt, f1) and get to the control center, I can't seem tpo change the xubuntu icon that used to be a computer, or the window colors.... perhaps a tip to get into the xubuntu control center at login???)

- Compiz works brilliantly in Gnome, but even with everything enabled in the settings, it refuses (after log-out/in and reboot) to do the cube, switch workspaces, wobbly windows, everything. The driver is working for the video card of course.

- Icons in each owrkspace are the same in the menus. I read a warning that this would happen, but I was curious if I changed the icons in the menus in Xfce or gnome or KDE, will it apply to all environments?

- And finally, there are two options for XFCE in the desktop environment selector (login screen)... maybe i installed it twice?

Other than that, I don't really know of anything else I'm running into, I say again I love this OS, and am not afraid of a terminal, package managers, or whatever else anymore. Again, I do have the Karmic Koala running my machine..... and love it....

Oh, a random question(s) if anyone knows, I have KMail and use it often, but I realized too late it takes everything off the server when fetching.... and I turned that off, but I wonder if there's any way to put it back on the server beside emailing it to myself? And can Mac OS X run in VirtualBox? I've heard mixed opinions/stories... and I know these are off topic but just wonderin :)

Thanks again everyone

---

### Post by 3Miro on 2010-01-14
I use all three environments, but don't seem to have your issues.

- I cannot help with the splash screen, I do get Kubuntu, but I don't care so I did not try to check. You can read on how to set up your own splash screen.

- Gnome and XFCE icons are the same, but you can install different icon themes in both and make them different (that is what I did). KDE was totally separate with its own icons and themes. KDE generally used different applications than Gnome and XFCE, so I guess if you try to run a Gnome app under KDE you might get it with t he Gnome icon, but KDE app icons are controlled via the KDE themes.

- Most of the start up programs in XFCE and Gnome would be the same and I don't know if you can make them separate. KDE is separate again, I do not get the same start up apps under KDE.

- Compiz: If compiz runs brilliantly under Gnome, I take it you have a problem getting it to work under KDE and/or XFCE. Compiz can run with KDE, but you are better off using Kwin, got to System Settings -> Desktop -> Effects and enable cube/wobbyness/whatever. XFCE's philosophy is small, fast, fast and using compiz with all the fluff seems a contradiction. I find for myself that the XFCE manager works great and it even supports simple transparency effects (no cube). You will have to read up on how to specifically enable Compiz under Gnome and KDE. I had it working with KDE long time ago, so my information would be outdated.

- The mail question is a trap that many people fall for in Thunderbird and I guess KMail. In Thunderbird you can  make all the messages as attachments and e-mail them back to you (it is faster than to e-mail them one at a time), I don't know about KMail.

- It is illegal to run Mac OS on anything other than Mac Hardware (including virtual box). I disagree with Apple's policy, and personally I have only used windows and Linux under VB, however, since Ubuntu is trying to play nice, you will probably  not get any advice ion how to do this here (or on any "official" web site).

---

### Post by JiuJitsu500 on 2010-01-15
Awesome reply man.... But I realized most of my problems were from laziness... All I had to do was install KWin like you said, log out, then it switched to it automatically. Then I did Compiz in KDE through some screwin around, and got both working (not at the same time of course). Thanks for that. And Xfce is my work desktop, I shouldn't have included that in the Compiz stuff, I didn't want it there sorry....

 I fixed the splash screen(s) by going into the root files and finding out the Grub Splash was easily changable by install startup manager in the terminal (sudo apt-get install startupmanager) and going back to Ubuntu.....

But now I'm struggling with one last thing.... the login screen is still screwy. Xfce, from what I understand, in the new versions of ubuntu, uses GDM still to control it.... So by opening a terminal at login, and getting to the control center and changing appearence and what not, it SHOULD change it, like it used to...

But, something else is there, even in the root files I can't find it, GDM didn't work, and I'm lost still. I'm googling and editing, but still no luck.... anyone have ideas on what's up with Xfce's login when gnome and KDE are on the same platform?

As for seperate startup apps.... I found a ver inefficient way.... going into startup scripts and adding "ShowOnlyIn=GNOME" or KDE, XFCE.... it suck, but Cairo Dock is the only one I'm after right now.... but the icons thing is still annoying... I have to fiddle with it but I think I found some programs....

And the KMail crap, you're right... a trap and it's annoying. Thanks for the thunderbird tip, I'll give that a go. And Mac stuff.... I didn't know it was illegal. So I'll "not" ask anymore in official sources ;) , but the OSx86 guys answered most of my questions... Thanks though.

---

### Post by JiuJitsu500 on 2010-01-15
UPDATE

In a day now I've managed to do a lot with all this, turns out I already knew how to do most of it... I got KDE working fantastic, and Xfce is sweet too.... now Gnome is to show off to people (cube, cairo, all that good stuff) because it's what I'm used to and had it first.

KDE is prettier, and a lot more complicated to me, but is a play-around desktop for me because I don't know it yet... but to edit startup scripts or anything this is definately what I use (graphic interface is easier than Xfce, tough mostly the same) because Dolphin is more useful than Nautilus to me.

For work and speed, by far Xfce is the way to go. It logs in in like a second and a half. I guess it's what it's designed for.... but does everything better than I thought it would.

The only problem is boot time now rivals Windows because of the environments butting heads at times, but it still all works flawlessly.... and once I separated start-up applications (in Dolphin, adding OnlyShowIn= in the scripts) and got things going.... I can't ask for a better computer.

But, one thing still eludes me.... with all thre going, does GDM not configure the log-in window? Everything else is great, but the window color is still all Xubuntu themed (including the xubuntu logo where the computer icon should be), and I can't get it changed yet.... anyone have any advice on this one?

---

