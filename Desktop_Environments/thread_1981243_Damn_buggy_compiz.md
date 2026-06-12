---
title: "Damn buggy compiz"
date: 2012-05-16
forum: Desktop Environments
---

### Post by mmerlone on 2012-05-16
Hi folks,

I am using Ubuntu on my desktop for many years now, and 12.04 seems to be the most buggy compiz ever! I use dual monitor setup in TwinView with an nvidia card, and no matter the driver I use (nouveau or nvidia proprietary) I have at least one extremely annoying bug on compiz. This is said to be the best ubuntu ever, but is not. I am using official latest compiz, unity, gnome, etc for 12.04. Machine is a i5 with a nvidia gt9500 but this is irrelevant. It happens with Unity and Gnome, irrelevant.

The bug happens when moved windows across workspaces using ctrl+alt+shift+arrow get erratic behavior, moving back alone to another workspace and position (sometimes the same position, but not always). For example: I have a terminal window, which I set to be on the monitor 2 of the first workspace. I ctrl+alt+kp9 the window (grid plugin) so it stays at the top right corner of the monitor. Then I ctrl+alt+arrow to go back to the the workspace 2 and there is the terminal window on the top-left (!) corner of the first monitor! I get back to first workspace and the window is not there anymore (sure, it got to the other workspace by it self). When I put that window back where I want it to be, I notice my Eclipse application got to workspace 2 when it was on workspace 3 (5 workspaces total).

Even worst, many times, I try to catch the window with alt+click to put it back where it was and compiz does not know the window is there! It grabs the window below! I have to use the scale plugin, for instance, to put the focus on the window so I can grab it.

I know I should fill a bug and I will. But had to come here register my dissatisfaction since I found nothing similar this on the net, very few ubuntu 12.04 reviews, comments and whatsoever so I assume ubuntu is cooling on the community or the community is loosing faith and getting used to those pesky desktop unity+compiz bugs.

This happens since 11.10, feel like those desktop bugs are increasing since 11.04 and those long-term annoying bugs make feeel like going back to debian or freebsd. I upgraded from 11.10 in a hope to have those bugs corrected, but got worse.

Going to file the bug now. I am available to provide more info, test something, whatever.

Best regards.

---

### Post by mmerlone on 2012-05-16
Reported: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1000367](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1000367)

---

### Post by mbojan on 2012-06-05
Thanks for reporting this. I'm getting the same type of crazy behavior without multiple monitors, just on my laptop... I hope compiz developers will be able to fix that soon.

For me upgrading to 12.04 from Natty broke many things, grid plugin being one of the most essential broken items...

---

### Post by UltimateCat on 2012-06-05
I too have had my share of buggy stuff with compiz.

When I switched from a track ball mouse to a regular wireless mouse I lost some of the functionalities that I use in GIMP to perform certain desired effects.

Before I switched mice I stopped using proprietary drivers and never had another problem with Compiz.

Looking forward to solutions for a lot less buggy-ness.

---

### Post by XxionxX on 2012-10-11
You can fix this by disabling the 'place windows' plugin (just un-tick the box). It is located under 'Window Management'. See pic:

[IMG]http://i.imgur.com/wgquI.png[/IMG]
[IMG]http://imgur.com/wgquI[/IMG]

---

