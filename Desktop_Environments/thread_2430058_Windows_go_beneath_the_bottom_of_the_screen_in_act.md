---
title: "Windows go beneath the bottom of the screen in activities view."
date: 2019-10-27
forum: Desktop Environments
---

### Post by Rajah_Brooke on 2019-10-27
Hi all,

I've come across a very minor bug, but since it's the only problem I've come across in 19.10 so far, it's really been annoying me.

When I activate "Activities" view in the default session of Ubuntu (Window spread), under certain circumstances, the bottoms of the windows, including the the title-bar text, go below the visible area. 

This specifically happens when there is one full-screened window on the workspace, or if there are 3-5 open windows on the workspace. If there are only two, or more than five, windows spread as they should. 

[Here's a screenshot ]("https://i.imgur.com/HN682tm.png")of this on my desktop. This is also visible on OMG Ubuntu's "Ubuntu 19.10: What's New?" [video on YouTube]("https://youtu.be/4YywtDfnDI8?t=165"). So it's not unique to my system.

I came across this issue on 19.04, but didn't post here because I reckoned it would be fixed in 19.10. 

Any ideas how I could fix this? I would also like to post a bug report on launchpad, but I'm not sure how to explain the problem, so any help where that's concerned would also be much appreciated.

Thanks!

---

### Post by tojonukokhadush on 2019-10-27
similar problem in my ubuntu 19.10 system as well, but its with the window display on the main screen:

[https://ubuntuforums.org/showthread.php?t=2430050](https://ubuntuforums.org/showthread.php?t=2430050)

hope they would acknowledge these issues. 19.10 seems to have many silly issues.

---

### Post by deadflowr on 2019-10-27
> **Rajah_Brooke said:**
> Hi all,

I've come across a very minor bug, but since it's the only problem I've come across in 19.10 so far, it's really been annoying me.

When I activate "Activities" view in the default session of Ubuntu (Window spread), under certain circumstances, the bottoms of the windows, including the the title-bar text, go below the visible area. 

This specifically happens when there is one full-screened window on the workspace, or if there are 3-5 open windows on the workspace. If there are only two, or more than five, windows spread as they should. 

[Here's a screenshot ]("https://i.imgur.com/HN682tm.png")of this on my desktop. This is also visible on OMG Ubuntu's "Ubuntu 19.10: What's New?" [video on YouTube]("https://youtu.be/4YywtDfnDI8?t=165"). So it's not unique to my system.

I came across this issue on 19.04, but didn't post here because I reckoned it would be fixed in 19.10. 

Any ideas how I could fix this? I would also like to post a bug report on launchpad, but I'm not sure how to explain the problem, so any help where that's concerned would also be much appreciated.

Thanks!

You seems to have this bug (and duplicate):
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1844529]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1844529")
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/+bug/1834967]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/+bug/1834967")
and a discussion of it is over here:
[https://discourse.ubuntu.com/t/the-gnome-3-34-migration-what-are-your-bugs/12348/27]("https://discourse.ubuntu.com/t/the-gnome-3-34-migration-what-are-your-bugs/12348/27")

---

### Post by Rajah_Brooke on 2019-10-27
Thanks for the reply, I will be following the discussion. Since posting here, I have found a duplicate bug on LaunchPad [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1834967"). I hope they fix this, because it really detracts from the overall professionalism of the desktop.

---

