---
title: "Remote login to headless 10.10 problem"
date: 2011-04-10
forum: Desktop Environments
---

### Post by nmw01223 on 2011-04-10
I'm a complete beginner at this apart from messing with a Linux box 10 years ago as a software developer. Only installed ubuntu 10.10 a day and a half ago to see what I can do with it. Installed remarkably painlessly.

I want to run this sans mouse/keyboard/monitor for various reasons. Followed this thread [http://blog.sarah-happy.ca/2010/10/ubuntu-1010-vnc-login-screen.html?showComment=1300995910058#c2741912386263492003](http://blog.sarah-happy.ca/2010/10/ubuntu-1010-vnc-login-screen.html?showComment=1300995910058#c2741912386263492003) slavishly as I don't know what I doing (uses Xvnc), and it all works fine (using TightVNC as the viewer on a remote Windows PC) except:

[LIST=1]
[*]Default size is 1024x768. As soon as I add a geometry parameter to server_args (-geometry 1280x1024), I get a blank grey window with no login prompt. Can't find a way around this so I'm stuck with 1024x768 if I want the login prompt (which of course I do).
[*]I can't shut it down remotely (never mind why I want to - I do). If I click the power then shutdown menu item, the TightVNC session closes but the box doesn't shut down. It seems I can only do that from the actual box.
[/LIST]
Any suggestions?

STOP PRESS: Found I have bigger problems - if I don't have a keyboard/mouse/monitor (not sure which or all) fitted to the remote box, no login prompt again regardless of geometry.

---

