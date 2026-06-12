---
title: "Compiz broken after upgrade to gutsy"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by toby_1_kenobi on 2007-10-20
I was running fiesty with compiz fusion working fine (from trevino repositories) and then I upgraded to gutsy using the recommended method, and Compiz doesn't work.

Before anyone points it out to me I know there is a sticky in this forum warning about this, but I didn't go to this forum before upgrading. A pity that info isn't in the [release notes]("http://www.ubuntulinux.org/getubuntu/releasenotes/710"), which I read thoroughly before upgrading. 

Anyway, the problem is that windows and menus don't appear, instead the background shifts in the area where they would appear. This makes the desktop unusable. I can log into the falisafe gnome session and everything's fine.

I got a helpful info message telling me that I didn't need to have my own compiz thing happening because it's part of the operating system now, so I turned off the script that launched config on start up, restarted X and got to the metacity desktop. Then I found out where to turn on the effects in the menus thinking that the if I went through the standard way it would work, but it didn't. Still the same problem, except this time I don't know how to turn it off. The normal gnome session is unuseable, and I can't turn it off through the failsafe gnome session menus.

If anyone could help me out that would be great. I think I have a standard intel graphics card.

**update**: I've managed to get my visual effects to "none" in my main session, by uninstalling all packages with "compiz" in the name and then deleting everything under ~/.config/ that mentions compiz, then going back to my normal gnome session and reinstalling the compiz packages. However even with visual affects on "none" I still get problems with the display not being redrawn properly when I move a window around. Everything still works fine in the failsafe session. I don't know what's wrong.

**update 2**: I've found that the problem with the display goes away when I increase my screen resolution from 1024x768 with 85hz to 1280x1024 where the only available refresh rate is 60hz. But I don't like this resolution and I don't think the refresh rate is right because everything is a bit jerky. Anyway this discovery makes me think the problem lies in my xorg.conf file, which I remember editing to set up 3D effects in feisty.

Any help at all would be much appreciated

**update 3**: I think I've worked out it's probably the monitor settings. I've been fiddling with the "screen and graphics" tool. My monitor is not listed in it, so I've been trying various different generic options. I've been getting closer to what I want, but the windows are still pretty jerky when dragged around and everything seems to happen more slowly. Anyway the failsafe gnome session seems to work perfectly so if I knew what monitor settings that uses I'd be fine.

Does anyone know what monitor settings failsafe gnome uses?

Why do I feel like I'm the only one whose questions are never answered?

---

