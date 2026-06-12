---
title: "Q: how do different DEs implement workspaces?"
date: 2018-04-25
forum: Desktop Environments
---

### Post by Skaperen on 2018-04-25
**how do different desktop environments implement workspaces?**

i'm currently running *Unity* under _Ubuntu Xenial 16.04 LTS_ with workspaces enabled for several users on the system.  but when i try various tests around the workspaces, i can't really see how it's being done.  i see only one X server process per user, so it's not being done by multiple servers.  an old way i saw this done in X a couple decades ago was by a larger buffer (a few times larger than the monitor) and a limited display of that buffer (same size as the monitor).  apparently, switching workspace involved getting X to change which part of the buffer was displayed.  different windows ended up at different geometry positions.  by knowing the real display size and virtual display size, it was possible to open a window into a specific workspace.  i automated the startup of a lot of that.

the previous distro i used was *Slackware*.  i customized it by expanding the number of virtual (text) consoles and mapping every combination of Alt+Ctrl+some-other-key to its own virtual console.  10 of them ran X under various user names.  the remaining text consoles stayed in text mode at a rather high number of columns and rows (i don't remember the exact size, but i could go to 238x190 which was too small to read, so i had a size somewhere between 80x36 and that).  i could switch virtual consoles with an Alt+Ctrl+some-other-key press.  then within each of the 10 X servers i had 40 workspaces done that old way.  i'd ofter have over 200 shell sessions running.  i'd probably have had more if i was running *screen* back then.

i used multiple userids then and use them now as a clear and obvious isolation between projects and/or web browsing.  for example LinkedIn is browsed in its own userid because i have seen them trying to discover other places i have visited.   a few others are fully isolated and many are semi-isolated.

in a future DE i want to have easy workspace switching and userid switching.  if this is done by workspace->userid and there are plenty of those in total then that would be a good way for me.

i've been thinking lately about doing switching of many X servers by [VNC]("https://en.wikipedia.org/wiki/Virtual_Network_Computing").  what i would do is program my own VNC switcher.  one or more clients would connect to it by VNC and it would connect by VNC to many X servers running with a VNC connectable virtual display.  this would let me spread workspaces out over the network to many machines and cloud instances (encryption needed).  i would have to invent some means to deploy buttons to click on to do the switching, and a way to specify where to connect to (and an automation API).

this post is already too long ... more later.

---

### Post by kerry_s on 2018-04-28
i think i just played with your perfect setup, might become mine to.
it's ubuntu-budgie 18 you should grab a live & play with it a bit.
check out the video on the release page.
[https://ubuntubudgie.org/blog/2018/03/08/18-04-release-notes](https://ubuntubudgie.org/blog/2018/03/08/18-04-release-notes)

don't just consider the ui, you can make it look like unity if you want.
check out the dynamic workspaces(create on the fly), the shuffle app you can grid apps(wow!), windows preview(pretty close to expose). 

for me i would just add devilspie2 to maximize the apps i want when launched. you might want to look into devilspie2 it's a lot easier to get apps where you want. i'm still learning it. but i seen a lot of example's for terminal placement & size.

i'll probably install later today, after i finish watching lucifer, i'm half way through season 3, can't stop right now. lol

---

### Post by Skaperen on 2018-04-28
it doesn't have to look like Unity.  the thing i want is the ability to make a lot of workspaces, where each individual workspace can be logged in as a different user (instead of all of them being the same user).  that means within that workspace, everything is running in processes that are running as that user, effective and real.  maybe switching to a workspace that has never been used before (since the main screen login) could get a standard login screen with a button for instant password-less login for the same user, also for other usernames which are configured for login-trust for this main user (i could go into more detail about this).

another important-to-me feature is a means to set up the active workspaces (which user logged in as and what applications are running) that has been saved, such as at main screen login time.  having this saved in an editable text file is also important to me (so i can make minor tweaks or write code that generates it.  JSON or XML may be options, here.

i'd also like to see this all work on XVNC which has a surprise for the DE: X is started before the DE.  DEs need to "learn" to work properly when they get start with X already running, such as XVNC or a login under X.  i've had problems with trying new DEs (perhaps because) i started (them) under XVNC as my "other environment" instead of a VM.

fyi, a "lot of workspaces" to me means at least 64 or better yet, 100.  i would like to make the key-combo window_key plus any one of every other key (including all mouse keys) be a unique workspace.  plus configurable graphical means to switch workspaces that can include a drop-down menu, graphical buttons, and side-fly-out (or whatever you guys call them) features.

---

