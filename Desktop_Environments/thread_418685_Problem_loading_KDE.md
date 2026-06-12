---
title: "Problem loading KDE"
date: 2007-04-22
forum: Desktop Environments
---

### Post by sideburnz17 on 2007-04-22
I posted this in 'Absolute beginner talk' before I found this section, so I apologize if this is overkill

I'm absolutely new to running Ubuntu or any Linux dist. on my machine, so bear with me.  A little embarassing- cuz i'm a software engineer (only ever dealt with CLI's)

When I turned on my computer today, X didn't start (I think the default is KDE, not GNOME?) and went straight to a command prompt. when i ran

start_kdeinit --new-startup +kcminit_startup

it said

DISPLAY not set.

So I looked around online and tried

exec xterm -geometry +0+0

Which apparently wasn't the right thing to do, because I got the same error (sort of - xterm Xt error: Can't open display)

startx works fine, but I prefer KDE to GNOME. What's going on, and how can I get KDE to work again, and how do I set it so that it takes me straight there instead of a command prompt (which happens every time now)?

Thanks in advance.

---

